# Privacy Policy for Talk 2 Me BB

**Last updated: 2026-04-22**

Talk 2 Me BB ("the app") is a baby tracking app for parents and caregivers. We take your family's privacy seriously. This policy explains what information the app uses, where it's stored, who else handles it, and what control you have.

## Short version

- You sign in with your **Apple ID** (via Sign in with Apple). We never see your Apple password.
- Your baby records (feedings, diaper changes, sleep sessions) are stored **on your device AND in a private database hosted by Supabase** so they can sync between the devices of caregivers you explicitly invite.
- The only people who can see your household's records are you and caregivers you've invited via share link. We (the developer) do not read or use your data.
- When you use voice input, the transcript is sent over HTTPS to a voice-parsing service so it can be turned into structured entries. The transcript is not retained.
- We do not use analytics, advertising, tracking, or any third-party SDK that collects personal data.
- You can **export all your data** or **delete your account and every byte of your data** any time from Settings → Danger Zone.

## What the app stores

**On your device, inside the app's private container:**

- Caregiver profile you set up (name, optional email, role)
- Baby profile(s) you add (name, optional birthday)
- Feeding, diaper change, and sleep entries you log
- App preferences (language, measurement unit, reminder settings)
- Optional Groq API key if you've entered one in Settings

**In our Supabase database, tied to your account:**

- The same records listed above, synced so they appear on every device you're signed into and on your invited caregivers' devices
- A reference to your Apple user identifier (an opaque ID Apple gives us — not your email, not your Apple password)
- Your display name and role label for the household UI, if you set them
- Invite codes you've generated for other caregivers (expire after 7 days or first redemption)

This data is also included in your standard iCloud device backup (encrypted by Apple) if you have iOS Backup enabled.

## Who else handles your data

We use the following third-party services ("processors"). Each only sees the data described:

### Supabase (database + authentication)

- Stores baby records, household memberships, and invite codes
- Verifies your Sign in with Apple token and issues the session that lets your device read/write your own data
- Does not sell, mine, or use your data for anything other than storing and serving it back to you
- Access to rows is gated by Postgres Row-Level Security — each row is readable only by users who are members of that household
- Provider: Supabase Inc., [supabase.com/privacy](https://supabase.com/privacy)

### Cloudflare (voice-parsing proxy)

- Receives your voice transcript (text, not audio) when you use voice input
- Forwards it to Groq's language-model API, returns the structured result, does not retain
- Used to protect our Groq API key and rate-limit by device
- Provider: Cloudflare, Inc., [cloudflare.com/privacypolicy](https://www.cloudflare.com/privacypolicy/)

### Groq (language-model inference)

- Receives your voice transcript (text) via the Cloudflare proxy
- Parses the transcript into structured feeding / diaper / sleep entries
- Does not retain transcripts for training or storage per Groq's policy
- Provider: Groq, Inc., [groq.com/privacy-policy](https://groq.com/privacy-policy/)

### Apple (Sign in with Apple + push notifications)

- Handles Sign in with Apple — we receive only an opaque user identifier and, if you choose to share it, your email
- Provides TestFlight + App Store Connect crash reporting (developer-only aggregate; no personal content)

## What we do NOT do

- No analytics SDKs (Firebase, Mixpanel, Amplitude, etc.)
- No advertising or attribution tracking
- No crash reporting beyond what Apple provides to developers
- No social features that expose your data to non-invited users
- No background data uploads other than syncing your own records between your own devices + invited caregivers
- We do not sell, share, or disclose your data to anyone other than the processors listed above, and then only for the purpose of running the app

## Children's privacy

This app is intended for use by parents, caregivers, and legal guardians to track their own children's feeding, diaper, and sleep patterns. It is not directed at children themselves and does not collect any data from children. All records are tied to a parent-provided baby profile and live under the parent's account.

## Permissions the app requests

- **Microphone** — only when you tap the record button, to capture a short voice note (auto-stops after 12–30 seconds based on how many babies you track). Nothing is recorded when the mic button is not active.
- **Speech Recognition** — Apple's built-in framework converts your voice to text. The transcript is then sent to the voice-parsing service described above; the raw audio never leaves your device.
- **Camera** — only when you open "Scan invite" to join another caregiver's household. We read QR codes; we don't save photos or video.
- **Notifications** — only if you enable reminders in Settings. Notifications are scheduled locally on your device.

## Your rights

### Access / portability (export)

- Tap **Settings → Export my data** to generate a JSON file containing every row we hold on you (babies, feedings, diapers, sleeps, household memberships). Share it to Files, iCloud Drive, Mail, or anywhere else.

### Deletion

- **Any single entry**: swipe left → Delete (with 5-second undo)
- **All entries for a baby**: Settings → Babies → tap the baby → Delete
- **All entries for your account**: Settings → Danger Zone → Erase all data
- **Your entire account + all cloud data**: Settings → Danger Zone → Delete my account → confirm. This removes your Supabase user row and every baby / entry / household row that would be orphaned by your departure. It's irreversible.

### Revocation of caregiver access

- Settings → Family → Manage caregiver access → swipe a caregiver's row → Remove. They lose access instantly on their device too.
- Or use the "Revoke all access" button to cut everyone except yourself in one tap.

## Data retention

- Your data is retained until you delete it (per-row, per-baby, per-account as above) or until you delete the app from all your devices for an extended period — in which case we may delete dormant accounts after 24 months of total inactivity.
- Deleted data is removed from live databases immediately; Supabase retains encrypted backups for up to 30 days for disaster recovery, after which it's permanently gone.

## Security

- All traffic is encrypted in transit (HTTPS + TLS 1.2+).
- Supabase stores rows in a managed Postgres instance with at-rest encryption.
- Access to your rows requires a valid JWT issued via your Sign in with Apple session; RLS policies reject requests that aren't from a household member.
- We rotate our API keys if compromised and notify affected users within 72 hours of discovery per standard breach-notification norms.

## Contact

For questions about this policy, to request an export beyond the in-app flow, or to request deletion: **kevha281@gmail.com**

## Changes

If we meaningfully change this policy, we'll update the "Last updated" date at the top and (for material changes) notify active users via an in-app notice.
