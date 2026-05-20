# Tides — Play Console Data Safety draft

**Last updated:** 2026-05-20
**Status:** Working draft. Copy these answers into the Play Console
**App content → Data safety** form. Re-check on the day of submission;
the Data safety form and the Privacy Policy must agree exactly.

---

## Section 1 — Data collection and security

### Does your app collect or share any of the required user data types?

**Yes.**

### Is all of the user data collected by your app encrypted in transit?

**Yes.** All traffic between the Tides app, the Tides API server (on
Railway, `eu-west`), and sub-processors (Google, OpenAI, Sentry,
Open-Meteo) is over HTTPS / TLS.

### Do you provide a way for users to request that their data is deleted?

**Yes.** In-app: **Settings → Your data → Delete my account.** Removes
the account from the live database immediately; rolling backups purge
within 30 days. The Privacy Policy section 7 + 8 documents this.

---

## Section 2 — Data types collected

For each row: **Collected? / Shared? / Optional? / Purposes / Why**

> Play's "Collected" = sent off the device. "Shared" = sent to a third
> party for that third party's own use. Sub-processors processing data
> on our behalf (Google Sign-In, Railway, OpenAI, Sentry, Open-Meteo)
> are **not** "sharing" under Play's definition.

### Personal info

| Data type | Collected | Shared | Optional | Purposes | Notes |
|---|---|---|---|---|---|
| Name | **Yes** | No | No (Google provides it) | Account management, App functionality | From Google Sign-In `name` claim. Displayed back in Settings. |
| Email address | **Yes** | No | No | Account management, App functionality | From Google Sign-In. Sign-in identifier. |
| User IDs | **Yes** | No | No | Account management, App functionality | Google `sub` claim stored as `googleId`. Internal user `cuid()`. |
| Address | No | — | — | — | — |
| Phone number | No | — | — | — | — |
| Race and ethnicity | No | — | — | — | — |
| Political or religious beliefs | No | — | — | — | — |
| Sexual orientation | No | — | — | — | — |
| Other info | **Yes** | No | **Yes (optional)** | App functionality, Personalization | Birth date / time / place — used for the natal chart and astrology-flavoured insights. Optional per onboarding. |

### Financial info

All rows: **No.** Tides is free in v1 and processes no payments.

### Health and fitness

| Data type | Collected | Shared | Notes |
|---|---|---|---|
| Health info | No | — | The mood reflection is not a health record; we do not infer health states from entries. See Privacy §3.2. |
| Fitness info | No | — | — |

### Messages

| Data type | Collected | Shared | Optional | Purposes | Notes |
|---|---|---|---|---|---|
| Emails | No | — | — | — | — |
| SMS or MMS | No | — | — | — | — |
| Other in-app messages | **Yes** | No | No (core feature) | App functionality, AI features | The mood reflection (one short sentence the user writes). Sent to OpenAI to generate the daily insight; OpenAI does not train on API inputs (per OpenAI policy as of last-updated). See Privacy §3.2 and §6.4. |

### Photos and videos / Audio files / Files and docs / Calendar / Contacts

All rows: **No.** No camera, microphone, photos, files, calendar, or
contacts permissions are declared in the Android manifest.

### App activity

| Data type | Collected | Shared | Notes |
|---|---|---|---|
| App interactions | No | — | No analytics SDK. No screen-view tracking. |
| In-app search history | No | — | — |
| Installed apps | No | — | — |
| Other user-generated content | **Yes** | No | The mood entry — intensity, descriptor, reflection, plus the captured sky context (weather snapshot, moon phase, transit positions). The reflection portion is the "Messages → Other in-app messages" row above. |
| Other actions | No | — | — |

### Web browsing / App info and performance / Device or other IDs

| Data type | Collected | Shared | Optional | Purposes | Notes |
|---|---|---|---|---|---|
| Web browsing history | No | — | — | — | — |
| Crash logs | **Yes** | No | No (no in-app opt-out yet — by email) | Analytics (in Play's taxonomy: app performance) | Sentry. **Not** tied to user identity — no `setUser`, no `sendDefaultPii`. Stack trace + device model + OS version + breadcrumbs of recent actions. EU region (Frankfurt). See Privacy §3.10 and §6.3. |
| Diagnostics | No | — | — | — | — |
| Other app performance data | No | — | — | — | — |
| Device or other IDs | No | — | — | — | No Android Advertising ID — `AD_ID` permission not requested. |

### Location

| Data type | Collected | Shared | Optional | Purposes | Notes |
|---|---|---|---|---|---|
| Approximate location | **Yes** | No | **Yes** | App functionality | The user's chosen current location (city / coords) is used to fetch weather and compute moon phase. Captured once at onboarding or in Settings — no background tracking, no subscription. |
| Precise location | **Yes** (when user taps "use my location") | No | **Yes** | App functionality | Same as above. The Android manifest declares COARSE + FINE because Expo Location requires it for the single `getCurrentPositionAsync` call. Foreground only. |

---

## Section 3 — Security practices

- **Data is encrypted in transit** — Yes (TLS for all API calls).
- **Users can request data deletion** — Yes (Settings → Your data →
  Delete my account; also by email).
- **You follow the Families Policy** — N/A (Tides is rated 13+, not
  primarily targeted at children).
- **Independent security review** — No.

---

## Cross-check against Privacy Policy

Before submitting, confirm:

- [ ] Every "Collected = Yes" row above is disclosed in Privacy §3.
- [ ] Every "Shared" answer matches Privacy §6 (no third-party sharing
      for their own purposes; sub-processors only).
- [ ] Purposes selected in Play match the lawful basis disclosed in
      Privacy §3 (Performance of contract for the journal; Consent for
      birth data; Legitimate interest for Sentry).
- [ ] The Privacy Policy URL field in Play Console points at the
      GitHub Pages URL: `https://tiago-o-pinheiro.github.io/tides-legal/privacy.html`
      (or the custom domain if you set one).

## Open questions for Tiago

- [ ] **Confirm Sentry opt-out path** in Play form: select "Data
      collection is required" because there's no in-app toggle yet.
      Reconsider when the v1.1 in-app toggle ships.
- [ ] **Confirm OpenAI processing disclosure.** The mood reflection
      goes to a US sub-processor under SCCs. The "Messages → Other
      in-app messages" row captures this. Lawyer review should confirm
      this is the correct Play taxonomy slot.
- [ ] **Re-grep before submission** for any new SDK, permission, or
      data flow added since this draft was written. The Data Safety
      form must match reality on the submission day.
