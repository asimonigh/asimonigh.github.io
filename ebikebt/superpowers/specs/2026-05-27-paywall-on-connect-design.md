# Paywall on Connect — Design

**Date:** 2026-05-27
**Status:** Approved (pending spec review)

## Problem

Today the RevenueCat paywall is a **global launch gate**: after onboarding, a
non-subscriber is routed straight to the paywall and cannot reach the e-bike
scan list at all. We want discovery to be free and the paywall to gate only the
act of **connecting** to a bike.

### Goals

- The app opens directly to the scan/discovery list (`SearchEbike`) regardless of
  subscription status. Scanning and seeing nearby bikes is free.
- Tapping **Connect** on a bike triggers the paywall when there is **no active
  subscription**.
- Connecting to a bike is **impossible** without an active subscription.

### Non-goals

- No auto-connect after purchase. After a successful purchase the user returns to
  the list and taps Connect again (now allowed).
- No launch-time / onboarding paywall. The paywall is reachable **only** via the
  Connect button.
- No change to the paywall UI, RevenueCat config, entitlement ID, or purchase
  flow itself.

## Current state (for reference)

- `App.kt:91-95` — `startDestination` routes to `Paywall` when `!isPro`.
- `App.kt:208` — `Permissions.onContinue` routes to `Paywall` when `!isPro`.
- `App.kt:98-111` — `LaunchedEffect(isPro)` forces the paywall back globally if
  entitlement is lost mid-session.
- `SearchEbikeViewModel.onEbikeClicked()` (127) calls `ebike.connect()` with no
  subscription check; "Connect" button (`SearchEbikeScreen:140`) wires to it.
- Paywall is a full-screen nav destination; on purchase `PaywallViewModel` emits
  `PaywallEvent.Unlocked` → `PaywallScreen.onUnlocked` → navigate to `SearchEbike`.
- `SubscriptionRepository.isPro: StateFlow<Boolean>` is the single source of truth
  (seeded from `appSettings.subscriptionActiveCache`, driven by RevenueCat; `true`
  in dev mode when RevenueCat is not configured).

## Design

The gate lives in the **ViewModel**, matching the existing event-driven pattern
(`SearchEbikeEvent.RequestBluetoothEnable`). The VM decides connect-vs-paywall and
emits an event; the screen forwards it to a navigation callback. This keeps the
decision testable and navigation out of the VM.

### 1. `App.kt` — move the trigger

- `startDestination`: remove the `!isPro -> Paywall` branch.
  ```kotlin
  val startDestination: Any =
      if (!appSettings.isOnboardingCompleted) EbikeBtDestination.Onboarding
      else EbikeBtDestination.SearchEbike
  ```
- `Permissions.onContinue`: always navigate to `SearchEbike` (remove the
  `if (isPro) ... else Paywall` branch).
- **Remove** the `LaunchedEffect(isPro)` block (98-111) that forces the paywall
  back globally — it contradicts "the app is usable without a subscription."
- `SearchEbike` composable: pass a new
  `onShowPaywall = { navController.navigate(EbikeBtDestination.Paywall) }`.
- `Paywall` composable: paywall now sits on top of `SearchEbike` in the back stack,
  so both exits pop back to the list:
  ```kotlin
  PaywallScreen(
      onUnlocked = { navController.popBackStack() },
      onClose = { navController.popBackStack() },
  )
  ```
  Passing a non-null `onClose` keeps the close (X) button visible so the user can
  dismiss the paywall and return to the list. Closing no longer quits the app.
- Remove the now-unused `koinInject<SubscriptionRepository>()` and
  `isPro` `collectAsState()` (and their imports) from `App.kt`.

### 2. `SearchEbikeViewModel.kt` — the gate

- Constructor gains `private val subscriptionRepository: SubscriptionRepository`.
- Add event: `data object ShowPaywall : SearchEbikeEvent`.
- In `onEbikeClicked(bike)`, after the `requireBluetooth()` check and before
  `Analytics.bikeConnectTap` / `ebike.connect()`:
  ```kotlin
  if (!subscriptionRepository.isPro.value) {
      Analytics.logEvent("paywall_triggered_connect", mapOf("bike" to bike.name))
      _events.tryEmit(SearchEbikeEvent.ShowPaywall)
      return
  }
  ```
- `onRequestDataClick()` (Start) needs **no** gate: the "Start" button only appears
  once a bike reaches `Ready`, which now requires a successful connect, which
  requires Pro.

### 3. `SearchEbikeScreen.kt` — forward the event

- Add `onShowPaywall: () -> Unit` to `SearchEbikeScreen` and thread it through
  `SearchEbikeReadyContent`.
- In the `events.collect` handler add:
  ```kotlin
  SearchEbikeEvent.ShowPaywall -> onShowPaywall()
  ```
- The "Connect" button keeps calling `viewModel.onEbikeClicked(bike)` unchanged —
  the VM decides whether to connect or emit `ShowPaywall`.

### 4. `AppModuleDI.kt` — inject the repository

```kotlin
single {
    (controller: PermissionsController) ->
        SearchEbikeViewModel(get(), get(), controller)
}
```
The second `get()` resolves the existing `SubscriptionRepository` single.

## Data flow

```
open app
  -> Onboarding (first run only) -> Permissions -> SearchEbike
  -> SearchEbike (scan list, free)
       tap Connect
         -> VM.onEbikeClicked
              isPro?  yes -> ebike.connect() -> ... -> Ready -> Start -> RideScreen
                      no  -> emit ShowPaywall -> navigate(Paywall)
                                                   purchase -> popBackStack -> SearchEbike
                                                   close    -> popBackStack -> SearchEbike
```

## Edge cases

- **Dev mode (no RevenueCat key):** `isPro` is `true`, so Connect works and the
  paywall never appears. Unchanged.
- **Entitlement lost while already connected/riding:** not re-gated. The global
  re-show is removed by design; only the *connect* action is gated. Acceptable —
  rare, and the requirement is about preventing connection without a subscription.
- **FakeEbike:** subject to the same gate in production (Pro required). Only used
  in dev, where `isPro` is `true`.

## Testing

No test infra exists in the repo. Verification is a manual build + run:
- `./gradlew :composeApp:compileDebugKotlinAndroid` compiles.
- Non-subscriber: app opens to scan list; tapping Connect shows the paywall;
  closing returns to the list; bike never connects.
- Subscriber (or dev mode): Connect proceeds to connection and Start as before.

## Affected files

- `composeApp/src/commonMain/kotlin/App.kt`
- `composeApp/src/commonMain/kotlin/feature/searchebike/SearchEbikeViewModel.kt`
- `composeApp/src/commonMain/kotlin/feature/searchebike/SearchEbikeScreen.kt`
- `composeApp/src/commonMain/kotlin/di/AppModuleDI.kt`
