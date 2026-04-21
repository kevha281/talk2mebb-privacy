# Privacy Policy for Talk 2 Me BB

**Last updated: 2026-04-20**

Talk 2 Me BB ("the app") is a baby tracking app for parents and caregivers. We take your family's privacy seriously. This policy explains what information the app uses, where it's stored, and what (if anything) leaves your device.

## Short version

- All baby records (feedings, diaper changes, sleep sessions) are stored **on your device only**.
- When you use the voice input feature, the transcript is sent over HTTPS to a voice-parsing service so it can be turned into structured entries. The transcript is not retained.
- We do not use analytics, advertising, tracking, or any third-party SDK that collects personal data.
- You can delete all your data at any time from Settings → Danger Zone.

## What the app stores

On your device, inside the app's private container:

- Caregiver profile you set up (name, optional email, role)
- Baby profile(s) you add (name, optional birthday)
- Feeding, diaper change, and sleep entries you log
- App preferences (language, measurement unit, reminder settings)
- Optional Groq API key if you've entered one in Settings

This data is included in your standard iCloud device backup (encrypted by Apple) if you have iOS Backup enabled — the same way your Notes or Reminders are backed up. We have no access to your backups.

## What leaves your device

Voice input sends the recognized transcript text to a voice-parsing service (Groq, or our hosted proxy built on Cloudflare Workers) over HTTPS. The service returns a structured JSON result (feeding, diaper, or sleep entries) and the request is not retained for training or storage on our end. A per-device daily rate limit prevents abuse.

No other data leaves your device. We do not operate servers that store your baby's records. We do not sell, share, or disclose your data to anyone.

## What we do NOT do

- No analytics SDKs (Firebase, Mixpanel, Amplitude, etc.)
- No advertising or attribution tracking
- No crash reporting beyond what Apple provides in TestFlight / App Store Connect for the developer only
- No social features, accounts, or logins
- No background data uploads

## Children's privacy

This app is intended for use by parents, caregivers, and legal guardians to track their own children's feeding, diaper, and sleep patterns. It is not directed at children themselves and does not collect any data from children. All records are tied to a parent-provided baby profile that lives on the parent's device.

## Permissions the app requests

- **Microphone** — only when you tap the record button, to capture a short voice note (auto-stops after 8–25 seconds based on how many babies you track). Nothing is recorded when the mic button is not active.
- **Speech Recognition** — performed on-device by Apple's built-in speech framework; converts your voice to text locally. That text is then sent to the voice-parsing service described above.
- **Notifications** — only if you enable reminders in Settings. Notifications are scheduled locally on your device; they never hit a server.

## Deletion

- Any single entry: swipe left → Delete (with 5-second undo)
- All entries at once: Settings → Danger Zone → Erase all data
- A single baby and all its records: Settings → Babies → tap the baby → Delete
- The entire app: delete the app from your home screen as you would any app — iOS removes all app data

## Contact

For questions about this policy, contact: **kevha281@gmail.com**

## Changes

If we meaningfully change this policy, we'll update the "Last updated" date at the top and (for material changes) notify active users via an in-app notice.
