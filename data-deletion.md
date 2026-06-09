---
title: Delete Your Tides Account
permalink: /data-deletion.html
---

# Tides — Delete Your Account and Data

**Last updated:** 2026-06-09
**Contact:** tiopioli89@gmail.com

---

## In short

Deleting your **Tides** account is something you can do yourself, in the app,
in a few taps. When you do, we remove your account and everything tied to it
from our live database straight away. A small number of things — anonymous
crash reports, rolling backups — rotate out on their own timetable, and we
explain those below.

- Open Tides → **Settings** → **Delete account**.
- That runs the deletion immediately on our database. No email, no waiting
  for us to approve it.
- Prefer to keep a copy first? Use **Settings → Export my data** to download
  your entries as a JSON file before you delete.
- Deleting your Tides account removes Tides' copy of your data. It does
  **not** touch your Google account — Tides only uses Google to sign you in.

---

## How to delete your account

Tides deletion is self-service and in-app. You do not need to email us or
wait for approval.

1. Open the **Tides** app and make sure you are signed in.
2. Go to **Settings**.
3. Tap **Delete account**.
4. Confirm. Your account and all the data listed below are deleted from our
   live database right away.

That is the whole flow. There is no separate web form to fill in, no support
ticket to wait on, and no "are you sure you want to give up your streak?"
guilt screen — Tides does not work that way.

### If you would rather email us

You do not have to use the in-app flow. You can also exercise your right to
erasure (Article 17 GDPR — the "right to be forgotten") by writing to
**tiopioli89@gmail.com**. Please put "Delete my account" in the subject line
and send it from the email address linked to your Tides account so we can
confirm the request is yours. We respond within one month, as required by
Article 12(3) GDPR.

### Export first, if you want to keep a copy

If you would like to keep your reflections before they are gone, use
**Settings → Export my data** (Article 20 GDPR — data portability). This
produces a JSON file with your entries that you can save wherever you like.
The export is unencrypted, so anyone with the file can read it — store it
somewhere you trust. Exporting is optional and entirely separate from
deletion.

### A note on Google Sign-In

Tides uses **Google Sign-In** only. Deleting your Tides account removes the
copy of your data that Tides holds. It does **not** delete or change your
Google account itself. If you also want to manage your Google account, you
do that in Google's own settings, not here.

---

## What gets deleted

When you delete your account, the following is removed within **30 days** of
the request. In practice it is deleted **immediately** from our live
database; the 30-day window only exists so that rolling backups can rotate
out. Deleted accounts are **never** restored from backups.

- **Account identity** — your email address, your Google account identifier,
  and your display name.
- **Journal and mood entries** — every mood check-in, intensity, descriptor,
  and free-text reflection you wrote.
- **Birth data and natal chart** — your birth date, time, and place, and the
  natal chart derived from them.
- **Location and weather** — your saved location and the weather snapshots
  stored alongside your entries.
- **Sky context** — the moon phase, transit positions, and other sky data
  captured with each entry.
- **Insights** — the daily and weekly insights generated for your account.
- **Notification preferences** — your per-trigger notification settings.
- **Authentication sessions** — the sign-in sessions and tokens that kept
  you logged in.

---

## What is kept, and for how long

A few things are not stored against your account in a way that an account
deletion can reach directly. None of them identify you after deletion. Here
is exactly what they are and when they disappear:

| What | Why it remains briefly | When it is gone |
|---|---|---|
| **Backups** | Railway-managed Postgres keeps rolling backups for disaster recovery. | The deleted account rotates out of backups within **30 days**. Never restored. |
| **Crash reports (Sentry)** | Anonymous crash and error reports that help us keep the app working. They contain **no** account identifier, so after deletion they are not tied to you. | Sentry's default retention, currently about **90 days**, then rotated out automatically. |
| **AI reflection text (OpenAI)** | The text of a reflection that was sent to OpenAI to generate an insight is held by OpenAI, **without any account identifier**, for abuse-monitoring. | Retained by OpenAI for up to **30 days**, then deleted. OpenAI does not train its models on it. |

In other words: your account and everything attached to it goes immediately;
backups catch up within 30 days; and the two third-party copies that exist
(crash reports, AI reflection text) carry no identifier and age out on their
own short timetables.

---

## Where to read more

The full detail on what we collect, why, the legal basis, and your rights
lives in our Privacy Policy:

- [Privacy Policy](./privacy.html) — see **"How long we keep your data"** and
  **"Your rights"** for the complete picture.

---

## Contact

- **Deletion and privacy questions:** tiopioli89@gmail.com
- **Controller:** Tiago Oliver Pinheiro Oliveira, Spain
