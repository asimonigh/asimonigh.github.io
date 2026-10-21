---
title: Privacy Policy
---

# Privacy Policy — MockRoute

_Last updated: 2026-10-21_

This Privacy Policy explains how the MockRoute mobile application ("the App", "we") handles information when you use it. The App is published by Anthony Simonigh ("the developer") and distributed through the Google Play Store.

The App requires **no user account**, shows **no ads** and uses **no analytics**. We have **no backend server**: your routes, places and settings stay **on your device**. Some features need an online service (the map, place search, road routing, subscriptions, crash reports). Section 2 lists exactly what each one receives.

---

## 1. Information processed locally on your device

The following information is used by the App and **stays on your device**:

- **Your real location**, read from Android location services, to show your position on the map and to offer it as a starting point ("My location").
- **Simulated locations**: the places and routes you choose, passed to Android as mock locations. While a simulation runs, the apps on your device receive the simulated position instead of your real one.
- **Saved routes**: GPX files and their index, in the App's private storage.
- **Recent places**: the last 8 places you picked in the search.
- **Settings**: simulation options (sources, altitude), onboarding and setup state, last known subscription state.

**GPX files** you import are read from the file you pick. Routes you export go only to the app you choose in the Android share sheet.

**Android backup**: the App allows Android's backup service. Depending on your device settings, Android may back up the data above to your Google account and restore it on a new device. This backup is handled by Google under your account settings, not by us.

---

## 2. Information sent to third parties

The App uses the following third-party services. Each service has its own privacy policy. All connections use HTTPS.

### 2.1 Map tiles — OpenFreeMap

To display the map, the App downloads map tiles from `tiles.openfreemap.org`. Each request reveals the map area and zoom level you are viewing and, as with any internet request, your IP address. OpenFreeMap states that its access logs do not contain IP addresses and that its server logs are deleted after 7 days.

OpenFreeMap privacy policy: <https://openfreemap.org/privacy/>
Map data © OpenStreetMap contributors.

### 2.2 Place search and road routing — Stadia Maps (Pro features)

- **Place search**: the App sends the text you type, the center of the map (to rank nearby results first) and your language to Stadia Maps, then the identifier of the place you pick to get its details.
- **Road routing**: the App sends the coordinates of your route's waypoints, then the computed route to get its altitudes. A waypoint can be your real location if you choose "My location".

Straight-line routes are computed on your device and send nothing. Stadia Maps states that its server logs are kept for about 7 to 14 days.

Stadia Maps privacy policy: <https://stadiamaps.com/privacy-policy/>

### 2.3 Google Play services location (Google LLC)

The App reads your real location through the Fused Location Provider of Google Play services. Google processes location data according to your device's location settings and Google's privacy policy.

Google's privacy policy: <https://policies.google.com/privacy>

### 2.4 RevenueCat (RevenueCat, Inc.)

We use RevenueCat to manage subscription purchases. When you start the App, RevenueCat generates an **anonymous identifier** (prefixed `$RCAnonymousID:`) on your device. This identifier is used to:

- Validate your subscription with Google Play
- Unlock Pro features in the App
- Restore your purchase if you reinstall the App

We do not send your name, email, location or any other personal data to RevenueCat.

RevenueCat privacy policy: <https://www.revenuecat.com/privacy>

### 2.5 Google Play Billing

When you subscribe, your transaction is processed by Google Play. Google Play shares with us only the information needed to validate your subscription (purchase token, product identifier, expiration date). We never receive your payment details.

### 2.6 Firebase Crashlytics (Google LLC)

When the App crashes, a crash report is sent to Firebase Crashlytics so we can fix the bug. The report contains:

- Device model, OS version, app version
- Stack trace and thread state at the moment of the crash
- A randomly generated installation ID (not linked to your identity)

It does **not** contain your location, your routes, your searches or any data you entered.

Google's privacy policy: <https://policies.google.com/privacy>
Firebase Crashlytics data handling: <https://firebase.google.com/support/privacy>

### 2.7 Support e-mail (sent only when you request it)

Tapping **"Contact support"** in Settings opens **your email app** with the App version, your device model and your Android version filled in. Nothing is sent unless you send the email yourself.

---

## 3. Permissions requested by the App

| Permission | Why we need it |
|---|---|
| Location (precise / approximate) | Show your real position on the map and offer it as a starting point |
| Mock location app (Developer options) | Provide the simulated position to Android. You select the App yourself in Developer options |
| Notifications | Show the notification of the running simulation |
| Foreground service (location) | Keep the simulation running while the App is in the background |
| Ignore battery optimizations (optional) | Prevent Android from stopping the simulation |
| Wake lock | Keep the simulation running when the screen is off |
| Internet | Map tiles, place search, road routing, subscriptions, crash reports |

The App does **not** request background location access.

---

## 4. Legal basis and retention

- **Legal basis** (EU/EEA — GDPR): performance of the service you request for the map, search, routing and subscription; our legitimate interest in fixing bugs for crash reports.
- **Retention**: we have no server and keep none of your data. The data on your device stays until you delete it or uninstall the App. Third parties keep data as described in section 2 and in their own policies.

---

## 5. Security

Your data is stored in the App's private storage, which other apps cannot read. Every request to a third-party service uses an encrypted HTTPS connection.

---

## 6. Children

The App is not directed to children under 13. We do not knowingly collect data from children.

---

## 7. Your rights

You can at any time:

- **Delete your data**: delete routes in the App, clear the App's storage in Android settings, or uninstall the App. Uninstalling deletes all local data and the anonymous RevenueCat ID.
- **Manage your subscription**: on the [Google Play subscriptions page](https://play.google.com/store/account/subscriptions).
- **Restore your purchase**: tap "Restore purchases" in the App's settings.
- **Request access to or deletion of crash data**: contact us at the email below.

Depending on your jurisdiction (EU/EEA — GDPR, California — CCPA), you may have additional rights, such as access, rectification, erasure, restriction, objection and portability. We will honor them on request. In the EU you can also lodge a complaint with your data protection authority (in France, the CNIL).

---

## 8. Changes to this policy

We may update this policy. The "Last updated" date at the top will reflect the change. Material changes will be announced in the App.

---

## 9. Contact

Questions or requests:

**Email:** [anthony.simonigh.pro@gmail.com](mailto:anthony.simonigh.pro@gmail.com)
**Developer:** Anthony Simonigh
