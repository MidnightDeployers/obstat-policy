---
---
# Privacy Policy for Obstat

**Effective date:** 2 September 2026

Obstat is a focus app that blocks the apps you choose until you complete a short challenge. This policy explains exactly what the app accesses and how it handles that information.

**In one line: everything you do in the app stays on your device. Obstat has no account and no servers of its own; the only time it uses the network is to process a paid emergency bypass purchase, through Google Play and RevenueCat.**

## At a glance

- No account, no sign-in, no cloud sync. Paid bypass purchases use an anonymous identifier — you never create an account.
- No analytics, no advertising, no tracking, and no third-party tracking components.
- The network is used for exactly one thing: processing paid emergency bypass purchases (fetching prices and validating receipts). Your rules, app list, usage, activity, and camera data are never transmitted.
- Everything the app stores lives only in its private storage on your phone, and you can erase all of it at any time. (Records of purchases you make also exist with Google Play and RevenueCat — see below.)

## Permissions, and why Obstat uses them

Each permission is requested only for the feature that needs it, and — apart from the purchase processing described under *Internet* below — everything it produces is used and kept on your device.

### Accessibility service

To block a protected app the moment it opens, Obstat uses an Android accessibility service. It reads only the *package identity* (for example, `com.instagram.android`) of the app currently in the foreground, and it is configured so that it cannot retrieve window content at all. That identity is checked against the apps you chose to protect; identities that are not on your list are discarded immediately and never stored. App content, messages, passwords, and on-screen text are never read.

### Camera

If you choose a push-up challenge, the camera is used only while that challenge or its readiness screen is on screen, and only to count your repetitions on the device. No image, video, or camera frame — and no body landmark derived from them — is ever saved, uploaded, or shared. The camera is released as soon as the challenge screen closes, and camera screens block screenshots and screen recording.

### Usage access

If you create a rule based on daily app usage, Obstat reads Android's app-usage events to measure how long your protected apps have been in the foreground. These events are filtered on your device down to only the apps you chose to protect; any other app's identity is discarded before anything is recorded. It stores a per-app daily total of foreground time, together with the rule and calendar day it belongs to.

### Physical activity / step counter

If you choose a movement challenge, Obstat reads your device's step counter while the challenge is active, to count steps toward your goal. It uses no location data, and it senses nothing outside a running challenge. It stores the challenge's goal and your verified progress toward it — enough to resume and confirm the challenge — and never a raw motion or location trail.

### Device authentication (biometric or screen lock)

The free emergency bypass — the first one each day — is protected by your device's own authentication. Android performs the check and returns only success or failure. Obstat never accesses, receives, or stores any biometric data such as a fingerprint or face image. (A paid bypass uses the Google Play purchase flow instead and involves no biometric data either.)

### Notifications and foreground service

During a movement challenge, Obstat shows an ongoing notification with your progress and Pause/Stop controls, and runs a foreground service so counting can continue while the screen is off. The notification shows only your step count versus your goal.

### Internet

Obstat uses the Internet permission for exactly one feature: processing paid emergency bypass purchases — fetching the current price and validating the purchase receipt — through Google Play. No other feature opens a network connection, and nothing else the app knows about you is ever transmitted. See *Network use* below for exactly who receives what.

## The list of apps on your device

To let you choose which apps to protect, Obstat asks Android for the list of apps that have a launcher icon, and reads each one's package name, display name, and a technical marker of when it was installed. Safety-critical apps — such as the system launcher, Settings, the dialer, and emergency apps — are filtered out and never shown. This list is read only while you are building or reviewing a rule; it is never uploaded, sold, or used for advertising. Obstat does **not** request the broad "query all packages" permission — it uses Android's scoped launcher visibility. Only the apps you actually select are kept (see below).

## What is stored on your device

Obstat stores the following only in its own private storage on your phone:

- Your rules and the apps you chose to protect — their package names, display names, and a technical marker used only to notice if a protected app was uninstalled and reinstalled.
- Your challenge attempts and progress, and the unlock grants that let a protected app through after a completed challenge.
- A record of each emergency bypass — free or paid — including, for paid ones, the Google Play product and order identifiers and the app that was unlocked. This record is the daily bypass counter and your durable local receipt.
- Per-app daily foreground-time totals, for rules that measure usage.
- A local activity history, and your preferences (such as your theme and your onboarding/consent record).

### How long it is kept

- **Historical records** — activity history, daily usage totals, completed usage intervals, and local bypass records — are removed automatically once they are older than 30 days (today plus the previous 29 days on your device's calendar). This clean-up runs the next time the app is active; older records are never shown in the meantime.
- **Purchase records for paid bypasses** also exist with Google Play and RevenueCat, which keep them under their own retention policies — Obstat cannot delete those on your behalf. Refunds are handled through Google Play.
- **Active enforcement data** — your rules, protected apps, in-progress attempts, and current grants — is kept for as long as the rule exists, so the app can keep enforcing it. It is removed when you delete the rule or use *Delete all local data*.
- **Preferences and your consent record** are kept until you change them, delete all local data, or uninstall the app.
- **Transient data** — camera frames, pose landmarks, live sensor readings, and the identity of the app currently in the foreground — is held only in memory while it is being used and is never written to long-term storage.

None of this data is included in Android cloud backup or device-to-device transfer — it is explicitly excluded from both.

## What Obstat never does

- It never reads or stores the content of your other apps — messages, passwords, on-screen text, or interface elements.
- It never stores or uploads camera images, video, frames, or body geometry.
- It never uses advertising identifiers, never sells your information, and shares nothing beyond the purchase data described below.
- It has no account, and no analytics, crash-reporting, or telemetry components; its only network use is the purchase processing described below.

## Network use: purchase processing only

Obstat's only use of the network is processing paid emergency bypass purchases — fetching the current price and validating the purchase receipt. Nothing else the app handles — your rules, your app list, usage history, activity, camera frames, or anything read by the accessibility service — is ever transmitted.

Exactly two parties receive purchase-related data:

- **Google Play** processes the payment itself. Your payment method is handled entirely by Google Play; Obstat never sees card numbers or any other payment instrument.
- **RevenueCat**, the purchase-processing service Obstat uses (acting as a processor on our behalf), receives an anonymous app user identifier (a random ID — you never create an account or sign in), your purchase receipts and tokens, and standard device metadata. It receives nothing else — no rules, app list, usage, or activity.

The app still contains no analytics, advertising, or telemetry: the billing library's own telemetry pipeline is excluded from the app at build time, in the same way as MediaPipe's. A build-time check fails the release if the app's merged manifest ever declares a permission outside a reviewed allowlist, or if any analytics or advertising transport component reappears. The app is built with third-party open-source libraries (including Google's MediaPipe pose model, which runs entirely on your device); apart from Google Play and RevenueCat as described here, none of them receive your information. It also includes the Source Sans 3 font under the SIL Open Font License.

## Your control over your data

- **Clear activity** removes your visible activity history while keeping what is needed for active rules.
- **Delete all local data** erases everything the app stores — rules, protected apps, attempts, grants, usage, activity, bypass records, onboarding consent, and preferences — turns the blocker off, resets the daily bypass ladder, and returns the app to its first-run state. It erases local data only: records of purchases you made are also held by Google Play and RevenueCat and are not erased by this action. Refunds go through Google Play.
- You can turn off the accessibility service at any time in Android Settings, or uninstall the app, which removes all of its data.

## Data deletion

Obstat (published by MidnightDeployers) gives you two ways to delete your data.

**On-device data — delete it yourself, instantly.** In the app, go to **Settings → Delete all local data**. This erases everything Obstat stores on your device: your rules, protected apps, challenge attempts, unlock grants, usage totals, activity history, bypass records, onboarding consent, and preferences. Uninstalling Obstat removes the same data. This data never leaves your device, so there is nothing else to request.

**Purchase records — request deletion by email.** If you bought a paid bypass, a record of it exists with Google Play and RevenueCat (see *Network use* above). To have it deleted:

1. Email **midnightdeployers@gmail.com** from the address associated with your purchase, and include the Google Play order number(s) you want removed.
2. We confirm your request and delete the associated records from RevenueCat.
3. You can also review or manage your purchases at any time in your Google Play account.

**What is kept:** Google Play retains the transaction records it is legally required to keep (for tax and accounting), under Google's own retention policies; MidnightDeployers cannot delete those. Everything else is deleted on request.

## Children's privacy

Obstat is a general-purpose focus tool and is not directed at children. It collects no personal information; the only data it transmits is the anonymous purchase processing described above, and payments themselves go through Google Play's own purchase flow.

## Changes to this policy

If this policy changes, the effective date above will be updated, and the summary shown inside the app will be updated to match.

## Contact

Obstat is published by MidnightDeployers. For any question about this policy or your data, contact [midnightdeployers@gmail.com](mailto:midnightdeployers@gmail.com).
