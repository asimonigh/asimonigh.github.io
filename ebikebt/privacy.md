---
title: Privacy Policy
---

# Privacy Policy — eBike Sync

_Last updated: 2026-04-30_

This Privacy Policy explains how the eBike Sync mobile application ("the App", "we") handles information when you use it. The App is published by Anthony Simonigh ("the developer") and distributed through the Google Play Store and the Apple App Store.

We designed eBike Sync to require **no user account**, collect **no personally identifiable information**, and keep your bike data **on your device**.

---

## 1. Information processed locally on your device

When you use the App, the following information is read from your e-bike or your phone and **stays on your device** — it is never transmitted to us or to any third party:

- Bike telemetry over Bluetooth Low Energy (BLE): speed, battery state of charge, assist mode, distance, motor power, cadence, error codes, IMU/orientation, and any other data exposed by the bike's protocol (Yamaha YEP, Yamaha STD200, Giant RideControl, BL60S/Mirror100).
- Bike identifiers advertised over BLE: device name, MAC address, manufacturer service UUIDs.
- App preferences: unit system (metric/imperial), onboarding completion flag, last known subscription state.

We do not store ride history on a remote server. We do not have a backend.

---

## 2. Information sent to third parties

The App uses the following third-party services. Each service has its own privacy policy.

### 2.1 Firebase Crashlytics (Google LLC)

When the App crashes, an anonymized crash report is sent to Firebase Crashlytics so we can fix the bug. The report contains:

- Device model, OS version, app version
- Stack trace and thread state at the moment of the crash
- A randomly generated installation ID (not linked to your identity)

It does **not** contain bike data, BLE addresses, or any data you entered.

Google's privacy policy: <https://policies.google.com/privacy>
Firebase Crashlytics data handling: <https://firebase.google.com/support/privacy>

### 2.2 Firebase Analytics (Google LLC)

The App reports anonymous usage events (e.g. "app_open", "bike_discovered", "ride_session_start") so we can understand how the App is used in aggregate. Events do **not** include bike names, BLE addresses, or precise location. A randomly generated installation ID is associated with these events.

You can disable Analytics by revoking the App's network access in your system settings.

### 2.3 RevenueCat (RevenueCat, Inc.)

We use RevenueCat to manage subscription purchases. When you start the App, RevenueCat generates an **anonymous identifier** (prefixed `$RCAnonymousID:`) on your device. This identifier is used to:

- Validate your subscription with the App Store / Google Play
- Unlock paid features in the App
- Restore your purchase if you reinstall the App

We do not send your name, email, or any personal data to RevenueCat. The App Store / Google Play handle the actual payment — we do not see your payment information.

RevenueCat privacy policy: <https://www.revenuecat.com/privacy>

### 2.4 Google Play Billing / Apple StoreKit

When you subscribe, your transaction is processed by Google Play (Android) or Apple StoreKit (iOS). They share with us only the information necessary to validate your subscription (purchase token, product identifier, expiration date). We never receive your payment details.

---

## 3. Permissions requested by the App

| Permission | Why we need it |
|---|---|
| Bluetooth (Scan / Connect) | Discover and communicate with your e-bike |
| Location (Coarse / Fine) | Required by Android < 12 to scan for BLE devices. We do **not** read or transmit your location. |
| Internet | Validate subscriptions, send crash reports |

The App declares `neverForLocation` on `BLUETOOTH_SCAN` (Android 12+), meaning the OS will not derive your location from BLE scan results.

---

## 4. Children

The App is not directed to children under 13. We do not knowingly collect data from children.

---

## 5. Your rights

You can at any time:

- **Stop sharing data**: uninstall the App. All local data and the anonymous RevenueCat ID are deleted.
- **Manage your subscription**: directly in the [Google Play subscriptions page](https://play.google.com/store/account/subscriptions) or in your iOS Settings.
- **Restore your purchase**: tap "Restore Purchases" in the App's settings.
- **Request deletion of crash data**: contact us at the email below.

Depending on your jurisdiction (EU/EEA — GDPR, California — CCPA), you may have additional rights. We will honor them on request.

---

## 6. Changes to this policy

We may update this policy. The "Last updated" date at the top will reflect the change. Material changes will be announced in the App.

---

## 7. Contact

Questions or requests:

**Email:** [anthony.simonigh.pro@gmail.com](mailto:anthony.simonigh.pro@gmail.com)
**Developer:** Anthony Simonigh
