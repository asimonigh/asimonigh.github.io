---
title: Privacy Policy
---

# Privacy Policy — eBike Sync

_Last updated: 2026-11-05_

This Privacy Policy explains how the eBike Sync mobile application ("the App", "we") handles information when you use it. The App is published by Anthony Simonigh ("the developer") and distributed through the Google Play Store and the Apple App Store.

We designed eBike Sync to require **no user account**, collect **no personally identifiable information**, and keep your bike data and your rides **on your device**. There are two exceptions, both under your control: a diagnostic log that **you can choose** to email to support to report a problem (see section 2.5), and live data that **you can choose** to share with other apps on your Android phone (see section 2.6).

---

## 1. Information processed locally on your device

When you use the App, the following information is read from your e-bike or your phone and **stays on your device**. We never transmit it automatically. It only leaves your device if **you** choose to send a diagnostic log to support (see section 2.5) or to share live data with other apps (see section 2.6):

- Bike telemetry over Bluetooth Low Energy (BLE): speed, battery state of charge, assist mode, distance, motor power, cadence, error codes, IMU/orientation, and any other data exposed by the bike's Bluetooth protocol.
- Bike identifiers advertised over BLE: device name, MAC address, manufacturer service UUIDs.
- Ride history: for each ride, the bike name, start and end times, distance, moving time, maximum speed and battery used. No GPS track is recorded.
- Your rear derailleur, if you add one: its identifier and last battery level, read from its Bluetooth advertisements without connecting to it.
- A random identifier that some bike systems ask for when the App connects. It is created on your phone and only sent to your bike.
- Your location, only when you select GPS as the speed source (Settings → Speed from). It is used live to compute your speed and is never stored or transmitted.
- App preferences: unit system (metric/imperial), speed source, automatic connection mode, last bike used, onboarding completion flag, last known subscription state.

We do not store ride history on a remote server. We do not have a backend.

---

## 2. Information sent to third parties

The App uses the following third-party services. Each service has its own privacy policy.

### 2.1 Firebase Crashlytics (Google LLC)

When the App crashes, an anonymized crash report is sent to Firebase Crashlytics so we can fix the bug. The report contains:

- Device model, OS version, app version
- Stack trace and thread state at the moment of the crash
- A randomly generated installation ID (not linked to your identity)

It does **not** contain bike telemetry, your ride history, or any data you entered.

Google's privacy policy: <https://policies.google.com/privacy>
Firebase Crashlytics data handling: <https://firebase.google.com/support/privacy>

### 2.2 Firebase Analytics (Google LLC)

The App reports anonymous usage events (e.g. "app_open", "bike_discovered", "ride_session_start") so we can understand how the App is used in aggregate. Events include the Bluetooth name of your bike. They do **not** include your location. A randomly generated installation ID is associated with these events.

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

### 2.5 Diagnostic logs (sent only when you request it)

To help diagnose Bluetooth connection problems, the App keeps a rolling debug log on your device (in the App's private storage). This log is **never sent automatically**. It leaves your device **only** when you tap **"Send logs to support"** in Settings, which opens **your email app** with the log attached so you can review it and send it to the developer (`ebikesyncapp@gmail.com`).

The log may contain:

- BLE connection events, handshake steps, errors and timeouts
- Bike identifiers (device name, BLE/MAC address, service UUIDs) and serial numbers (e.g. drive-unit serial, meter ID)
- Bike telemetry (speed, battery, assist mode, distance, motor power, etc.)
- When **"Detailed logs"** is enabled (Settings → Advanced, on by default), the raw BLE packets exchanged with the bike

You stay in control: turn off **"Detailed logs"** to exclude the raw packet data, and the email is sent only if you complete it in your email app. We use the log solely to investigate the issue you report.

### 2.6 Live data shared with other apps (Android, off by default)

If you turn on **"Share live data with other apps"** (Settings → Advanced), the App broadcasts live data to the apps installed on your phone that declare the matching permission: your bike's name and identifier, connection state, speed, cadence, battery, range, assist mode, motor power, trip distance and trip time. This data stays on your phone and never goes through the internet or through us. The apps that receive it handle it under their own privacy policies. Turn the option off to stop sharing.

---

## 3. Permissions requested by the App

| Permission | Why we need it |
|---|---|
| Bluetooth (Scan / Connect) | Discover and communicate with your e-bike, and read your rear derailleur's battery level |
| Location (Coarse / Fine) | Required by Android < 12 to scan for BLE devices. On Android and iOS, used for GPS speed only if you select it. Your location is never stored or transmitted. |
| Notifications | Show your ride in progress and the status of automatic start |
| Companion device and foreground service (Android) | Detect when your bike turns on and keep the connection while the App is in the background |
| Bluetooth in the background (iOS) | Keep the connection to your bike while the App is in the background |
| Internet | Validate subscriptions, send crash reports and usage events |

The App declares `neverForLocation` on `BLUETOOTH_SCAN` (Android 12+), meaning the OS will not derive your location from BLE scan results.

---

## 4. Children

The App is not directed to children under 13. We do not knowingly collect data from children.

---

## 5. Your rights

You can at any time:

- **Stop sharing data**: uninstall the App. All local data, including your ride history, and the anonymous RevenueCat ID are deleted.
- **Delete a ride**: in the App's Trips tab.
- **Stop using your location**: set Settings → Speed from back to Bike.
- **Stop sharing with other apps**: turn off "Share live data with other apps" in Settings.
- **Manage your subscription**: directly in the [Google Play subscriptions page](https://play.google.com/store/account/subscriptions) or in your iOS Settings.
- **Restore your purchase**: tap "Restore Purchases" in the App's settings.
- **Request deletion of crash data**: contact us at the email below.
- **Control diagnostic logs**: turn off "Detailed logs" in Settings to exclude raw packet data; a log only ever leaves your device if you email it to support yourself.

Depending on your jurisdiction (EU/EEA — GDPR, California — CCPA), you may have additional rights. We will honor them on request.

---

## 6. Changes to this policy

We may update this policy. The "Last updated" date at the top will reflect the change. Material changes will be announced in the App.

---

## 7. Contact

Questions or requests:

**Email:** [ebikesyncapp@gmail.com](mailto:ebikesyncapp@gmail.com)
**Developer:** Anthony Simonigh
