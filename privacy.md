---
title: Privacy Policy
permalink: /privacy.html
---

# Tides — Privacy Policy

**Last updated:** 2026-05-20
**Contact:** tiopioli89@gmail.com

---

## In short

We've tried to write this in a way you can actually read. Here is the whole
policy in eight bullets:

- Tides stores what you put into it — your mood check-ins, the sentence you
  wrote, the date and place we used to fetch the weather, and (if you gave
  us one) your birth date, time, and place.
- We use Google Sign-In, so we get your name and email from Google when you
  sign in. We do not see your Google password.
- We send the contents of your mood entry — your descriptor, your reflection
  sentence, and the sky around you — to OpenAI to generate the daily insight.
  OpenAI does not train its models on this data. If you do not want this,
  do not write a reflection you would not want a third party to process.
- We do not run analytics. We do not run ads. We do not sell or share your
  data. We do not track you across apps or websites.
- We collect anonymous crash reports through Sentry so we know when the app
  breaks. We do not attach your identity to these reports.
- You can export everything we have on you, in a JSON file, from Settings.
- You can delete your account from Settings. When you do, your data is
  permanently removed within 30 days.
- If anything in this document feels wrong to you, write to
  `tiopioli89@gmail.com`. A real person answers.

The rest of this document is the long form of those eight bullets, in the
language a regulator or a careful reader expects.

---

## 1. Who we are

Tides is built and operated by **Tiago Oliver Pinheiro Oliveira** as a solo
developer, based in Spain. For the purposes of the **General Data Protection
Regulation (Regulation (EU) 2016/679, "GDPR")** and Spain's **Ley Orgánica
3/2018 (LOPDGDD)**, Tiago Oliver Pinheiro Oliveira is the **data controller**
for all personal data processed through the Tides mobile application.

**Contact:**

- Email: `tiopioli89@gmail.com`
- Postal address: Carrer Provença 60, 08901 Hospitalet de Llobregat,
  Barcelona, Spain
- Country of establishment: Spain
- Supervisory authority: **Agencia Española de Protección de Datos (AEPD)**,
  C/ Jorge Juan, 6, 28001 Madrid, Spain — [www.aepd.es](https://www.aepd.es)

There is no statutory obligation to appoint a Data Protection Officer (DPO)
under Article 37 GDPR for an operation of Tides' size and scope. The contact
addresses above are the channel for any data-protection question.

---

## 2. What this policy covers

This policy describes how we process personal data when you use the **Tides
mobile application** for Android (and, in future versions, iOS). It applies
to the Tides app, the Tides server (hosted on Railway), and the sub-processors
named in **Section 6**.

It does not cover third-party services you reach by following a link out of
Tides (for example, the Google account screen for changing the email
associated with your sign-in). Those services have their own privacy
policies, which apply when you are inside them.

---

## 3. The data we collect, why, and the legal basis

We use the structure required by Article 13 GDPR: for each category of
personal data, we name _what_ we collect, _why_ we need it, the _lawful
basis_ under Article 6 GDPR, _where_ it is stored, and _how long_ we keep it.

### 3.1 Account identity

**What.** Your email address, your Google account identifier (`sub` claim
from the verified Google ID token), your display name, and (optionally) the
language and theme you chose during onboarding.

**Why.** To create and maintain your account, to authenticate you on
subsequent sessions, to send your data back to the device you sign in from,
and to set your in-app language to the one you chose.

**Lawful basis.** Article 6(1)(b) GDPR — _performance of a contract_ (you
asked us to host your journal, we need an account to do that). For the
language and theme, also Article 6(1)(a) — _consent_, because you can
change either at any time without consequence.

**Where stored.** Postgres database on Railway. See **Section 6** for the
hosting region and the cross-border-transfer mechanism.

**How long.** Until you delete your account. See **Section 8** for deletion
mechanics.

### 3.2 Your journal entries

**What.** Each mood check-in stores: an intensity value (1–5), a descriptor
word you picked from a fixed list, a free-text reflection (one short
sentence in your own words), and the timestamp at which the entry was
created.

**Why.** This _is_ the product. The mood entries are the journal Tides is
designed to keep for you. Without them, the app has nothing to show you on
the Journey screen.

**Lawful basis.** Article 6(1)(b) GDPR — _performance of a contract_.

**Special-category data (Article 9 GDPR).** A mood-journal reflection is
not, in itself, special-category data. However, a free-text field can
contain whatever a user chooses to write into it, including statements
that touch on physical or mental health, religious or philosophical
beliefs, or sexuality. **We do not infer health states from your entries.
We do not run any classifier over your reflection beyond what is needed to
hand it to the insight model.** If you do enter sensitive content, your
**right to erasure** in **Section 7** is unconditional and immediate, and
exporting + deleting your account removes that content from our database
within 30 days.

**Where stored.** Postgres database on Railway, in the `MoodEntry` table.

**How long.** Until you delete the entry (deletion of individual entries
is not exposed in v1 — see the **Open questions** at the foot of this
document) or until you delete your account.

### 3.3 Birth data (optional)

**What.** Your birth date, your birth time (in HH:MM format, 24-hour), and
the latitude/longitude/label of your place of birth.

**Why.** Tides uses your birth data to compute a natal chart and to
generate astrology-flavoured insights about how the current sky relates
to your chart. Birth data is _optional_. If you do not provide it, Tides
falls back to insights based only on the current sky.

**Lawful basis.** Article 6(1)(a) GDPR — _explicit consent_. You provide
this data during onboarding or in Settings; we treat that act as your
consent. You can withdraw consent at any time by clearing the birth fields
in Settings, which deletes the data from our database.

**Where stored.** Postgres database on Railway, in the `User` table. The
derived natal chart is stored alongside, as a JSON blob, so that it does
not need to be recomputed on every refresh.

**How long.** Until you remove it, or until you delete your account.

**Note on astrology.** Tides treats astrology as a reflective lens, not a
predictive system or a substitute for professional advice. See the
**Terms of Service**, Section 4, for the full astrology disclaimer. We do
not use your birth data for any purpose beyond computing your natal chart
and the insights you see in the app.

### 3.4 Current location (for weather)

**What.** The latitude, longitude, and a human-readable label (city or
place name) for your current location, captured once at onboarding or
updated in Settings.

**Why.** To look up the current weather at your location and to compute the
moon phase visible from your sky. This is the _current sky_ context that
sits under each entry in Tides.

**Lawful basis.** Article 6(1)(b) GDPR — _performance of a contract_.

**Important — we do not run continuous location tracking.** The Android
manifest declares `ACCESS_COARSE_LOCATION` and `ACCESS_FINE_LOCATION`
because the operating system requires the declaration even for a single
"get my current location" call. Tides never starts a background location
service, never subscribes to location updates, and never reads your
location without a deliberate action on your part (typing your address,
or tapping "use my current location" during onboarding).

**Where stored.** Postgres database on Railway, in the `User` table.

**How long.** Until you change it, clear it, or delete your account.

### 3.5 Weather snapshots

**What.** When you save a mood entry, the current weather at your
location — temperature, apparent temperature, a numeric WMO weather
code (the integer Open-Meteo uses to describe conditions, e.g. clear,
overcast, rain), cloud cover, precipitation, humidity, pressure, wind,
day/night, UV index, sunrise/sunset times — is fetched from Open-Meteo
and stored alongside the entry. The list is not personal data beyond
the fact that it ties to your location and the moment of your entry.

**Why.** The Journey screen shows you the weather as it was at the moment
of the entry. The Insights surface uses these snapshots to look for
patterns in how the weather relates to how you feel.

**Lawful basis.** Article 6(1)(b) GDPR — _performance of a contract_.

**Where stored.** Postgres database on Railway, in the `WeatherSnapshot`
table.

**How long.** Together with the entry it belongs to.

### 3.6 Sky context (transits, moon phase)

**What.** At the moment of each entry, Tides captures the position of the
Sun, Moon, Mercury, Venus, Mars, Jupiter, and Saturn (sign + degree),
plus the moon phase and illumination. When you have provided birth data,
the natal chart is also stored on your account.

**Why.** Same as above — context for the Journey screen and the insights
catalogue.

**Lawful basis.** Article 6(1)(b) GDPR — _performance of a contract_.

**Where stored.** Postgres database on Railway, in the `MoodEntry` and
`InsightItem` tables.

**How long.** Together with the entry it belongs to.

### 3.7 Generated insights

**What.** The title and body of each daily and weekly insight, the context
that produced it (a JSON blob containing your mood/descriptor/reflection
plus the sky context for that day), the language it was written in, and
whether it came from the AI model or from the canned fallback list.

**Why.** Insights are saved so you can revisit them on the Notice screen,
and so the same insight does not regenerate when the screen reloads.

**Lawful basis.** Article 6(1)(b) GDPR — _performance of a contract_.

**Where stored.** Postgres database on Railway, in the `InsightItem` table.

**How long.** Together with the user account.

### 3.8 Authentication state

**What.** A hashed refresh token, an optional user-agent string, the time
the session was created, the time it was last used, the time it expires,
and (if applicable) the time it was revoked.

**Why.** To keep you signed in on the device you signed in from, and to
allow you to sign out (revoking the refresh token) from Settings.

**Lawful basis.** Article 6(1)(b) GDPR — _performance of a contract_.

**Where stored.** Postgres database on Railway, in the `Session` table.

**How long.** Until you sign out, until the session expires, or until you
delete your account.

### 3.9 Notification preferences

**What.** Your per-trigger preferences for the in-app notifications surface
(moon-phase notifications on/off, new-insight notifications on/off).

**Why.** To honour what you chose during the Notifications onboarding step
and what you change in Settings.

**Lawful basis.** Article 6(1)(a) GDPR — _consent_ (notifications are
off by default; you opt in).

**Where stored.** Locally on your device. The Tides server does not
mirror your notification preferences; if you reinstall the app or
switch device, your preferences default to off and you re-opt in.

**How long.** Until you change them, until you uninstall the app, or
until you delete your account.

### 3.10 Crash and error reports (Sentry)

**What.** When the app crashes or throws an unhandled error, Sentry captures
a stack trace, the device model, the operating-system version, the app
version, and a list of recent in-app actions ("breadcrumbs" — e.g.,
"navigated to Today", "opened insight"). We do **not** attach your user
identifier, your email, your name, or any field from your account to these
reports. The Sentry init in `apps/mobile/index.ts` does not call
`Sentry.setUser` and does not enable `sendDefaultPii`.

**Why.** So that when something breaks for one user, we can fix it for
everyone before it breaks for the next.

**Lawful basis.** Article 6(1)(f) GDPR — _legitimate interest_. The
balancing test: we have a legitimate interest in keeping the app working;
crash data is the minimum we need to diagnose; we do not attach identities;
breadcrumbs may incidentally contain navigation strings but never the
contents of your entries. The balancing test favours processing. You have
the right to object under **Section 7**; opting out of crash reporting
is not exposed in v1 and is on the **Open questions** list.

**Where stored.** Sentry, EU region (`o*.ingest.de.sentry.io`, Frankfurt).
Sub-processor named in **Section 6**.

**How long.** Sentry's default retention (currently 90 days for the free
tier we are on).

### 3.11 What we do not collect

This list is part of the policy. If we add anything to this list, we will
update the policy and the **last updated** date at the top.

- **No analytics SDK.** No Mixpanel, no Amplitude, no PostHog, no Segment,
  no Firebase Analytics, no Adjust, no Bugsnag. We have not integrated a
  product-analytics library. We do not measure session length, screen
  views, retention, or feature usage. Play Console will show us aggregate
  install counts; that is the only retention signal we have.
- **No advertising identifiers.** We do not read your Android Advertising
  ID. We do not request the `AD_ID` permission. Tides has no advertising
  partners.
- **No background location.** See **Section 3.4**.
- **No biometric data.** We do not use device biometrics for sign-in. Sign
  in is Google Sign-In only.
- **No contacts, calendar, photos, microphone, or camera access.** The
  Android manifest does not declare these permissions. The `READ_EXTERNAL_STORAGE`
  and `WRITE_EXTERNAL_STORAGE` permissions are explicitly _blocked_ in
  `app.json`.
- **No social-graph data.** Tides has no friends list, no following, no
  sharing, no public profiles.
- **No data sales or cross-context behavioural advertising.** We do not
  sell, rent, or share your personal data with third parties for their
  own commercial purposes. The sub-processors in **Section 6** process
  your data only on our behalf and only for the purposes named.
- **No automated decision-making with legal or significant effects on
  you (Article 22 GDPR).** Tides shows you astrology-flavoured insights;
  it does not decide anything _about_ you, does not score you, does not
  grant or deny anything based on those insights, and does not modify
  your account state without your input.

---

## 4. What we will not do

Some of the things we do not do are not just absent — they are foreclosed
by how Tides is built. We list them here because what we _won't_ do is as
much of a privacy promise as what we _do_.

- **We will not run behavioural notifications.** Tides will never send
  you "you haven't logged today", "don't lose your streak", "your
  friends are journaling", or any message designed to pull you back
  into the app. Notifications are tied to environmental events (a new
  moon phase, a new insight) and are off by default. This is locked
  in the product philosophy, not a policy choice we could reverse
  without rewriting the app.
- **We will not gamify your reflection.** No streaks, no badges, no
  completion bars, no levelling, no leaderboards, no comparisons to
  other users.
- **We will not build social or sharing features in v1.** Tides is a
  private, solo tool. There is no public profile. There is no follow
  list. There is no way for another user to see what you wrote.
- **We will not introduce ads or paid placement in journaling content.**
  The product is free in v1. If we add a paid tier in v1.5 (a possibility
  flagged in our roadmap), it will be a straightforward subscription;
  it will not change what we collect.
- **We will not train AI models on your entries.** OpenAI's API policy
  (as of the last-updated date of this document) is that API inputs
  are not used to train its models, and we rely on that policy. We will
  not provide your entries to any third party for model training.
  If OpenAI's policy changes, we will either change provider or update
  this document and notify you before the change takes effect.

The word "never" in this section is used carefully. It means: _we will
not do this in any version of Tides without first updating this policy,
notifying you in the app, and giving you a chance to delete your account
before the change takes effect._

---

## 5. How long we keep your data

In short: until you delete your account.

In detail:

- **Account, journal entries, birth data, location, weather snapshots,
  sky context, insights, notification preferences** — kept while your
  account is active. Removed within 30 days of an account-deletion
  request. The 30-day window is the operational maximum; in practice the
  deletion runs immediately on the database, and the 30 days is a buffer
  for our backups to rotate out.
- **Authentication sessions** — kept until you sign out, until the session
  expires, or until you delete your account (whichever comes first).
- **Crash reports (Sentry)** — kept for Sentry's default retention,
  currently 90 days, then rotated out automatically. Crash reports do
  not contain account identifiers, so they are not tied to you after the
  fact.
- **Backups** — Railway's managed Postgres takes regular backups for
  disaster recovery. A deleted account is removed from the live database
  immediately; it will be purged from rolling backups within 30 days.
  We do not restore deleted accounts from backups under any circumstance.

---

## 6. Who else processes your data (sub-processors)

We use the following sub-processors. Each one processes your data only
on our behalf, only for the purpose named, and only to the extent
necessary for that purpose.

### 6.1 Google LLC (Google Sign-In)

- **Function.** Authenticates you. We receive your email, name, and a
  Google account identifier when you sign in. We do not receive your
  Google password.
- **Location of processing.** United States.
- **Transfer mechanism.** Google LLC is certified under the
  **EU–US Data Privacy Framework** as of 2023. This is the legal basis
  for the cross-border transfer of EU personal data to Google.
- **Their privacy policy.** [policies.google.com/privacy](https://policies.google.com/privacy)

### 6.2 Railway Corp (server + database hosting)

- **Function.** Hosts the Fastify API server and the Postgres database
  that stores your account, your entries, and everything else listed in
  **Section 3**.
- **Location of processing.** European Union (`eu-west`).
- **Transfer mechanism.** None required — processing stays in the EU.
  Encryption in transit (TLS) and at rest (managed Postgres) applies as
  a baseline security measure.
- **Their privacy policy.** [railway.com/legal/privacy](https://railway.com/legal/privacy)

### 6.3 Functional Software, Inc. ("Sentry")

- **Function.** Anonymous crash and error reporting. See **Section 3.10**
  for what is and is not sent.
- **Location of processing.** European Union (Frankfurt). The DSN points
  at `o*.ingest.de.sentry.io`.
- **Transfer mechanism.** None required — processing stays in the EU.
- **Their privacy policy.** [sentry.io/privacy](https://sentry.io/privacy)

### 6.4 OpenAI, L.L.C.

- **Function.** Generates the title and body of each daily and weekly
  insight using the `gpt-4o-mini` model. The prompt we send contains:
  the date, your mood intensity label (e.g., "steady (2)"), the
  descriptor word you picked, your free-text reflection sentence
  (verbatim), and the sky context for that day (weather summary, moon
  phase, transit positions). We do **not** send your name, email,
  Google account identifier, location coordinates, or birth data.
- **Location of processing.** United States.
- **Transfer mechanism.** **Standard Contractual Clauses (SCCs)** under
  Commission Implementing Decision (EU) 2021/914. OpenAI's data
  processing addendum (DPA) is the contractual layer.
- **What OpenAI does with this data.** Per OpenAI's API platform terms
  (as of the last-updated date of this document), API inputs and outputs
  are _not_ used to train OpenAI's models. OpenAI retains inputs and
  outputs for up to 30 days for abuse-monitoring purposes, then deletes
  them. We rely on this policy. If OpenAI's policy changes in a way that
  would meaningfully affect this disclosure, we will either change
  provider or update this policy and notify you before the change takes
  effect.
- **Their privacy policy.** [openai.com/policies/privacy-policy](https://openai.com/policies/privacy-policy)

**If you do not want your reflections processed by OpenAI**, the safest
action in v1 is to keep your reflection field empty. We are aware this is
not a fine-grained control; an opt-out toggle is on the **Open questions**
list at the foot of this document.

### 6.5 Open-Meteo

- **Function.** Public weather API. We send latitude and longitude only;
  no identifier, no account, no header that could tie a request back to
  you. Open-Meteo is arguably not a sub-processor under GDPR (no personal
  data leaves us) but we list it here so the data egress is on the record.
- **Location of processing.** European Union (Germany).
- **Their privacy policy.** [open-meteo.com/en/privacy](https://open-meteo.com/en/privacy)

We do not engage any other sub-processor. If we add one, we will update
this document and the **last updated** date.

---

## 7. Your rights

Under GDPR, you have the following rights with respect to your personal
data. We honour them at no cost, in any of the four languages Tides
supports (ES, CA, PT-BR, EN), within one month of your request (Article
12(3) GDPR).

- **Right of access (Article 15)** — to ask us what data we hold about
  you and to receive a copy.
- **Right to rectification (Article 16)** — to ask us to correct
  inaccurate data.
- **Right to erasure (Article 17, "right to be forgotten")** — to ask
  us to delete your data. Using **Delete account** in Settings exercises
  this right directly.
- **Right to restriction of processing (Article 18)** — to ask us to
  stop processing your data while a dispute is resolved.
- **Right to data portability (Article 20)** — to receive your data in
  a structured, commonly used, machine-readable format. **Export my data**
  in Settings exercises this right directly; the format is JSON.
- **Right to object (Article 21)** — to object to processing based on
  legitimate interest (in Tides' case, the Sentry crash-reporting flow).
  An in-app opt-out is on the **Open questions** list; until it ships,
  you can object by email and we will exclude your device from crash
  reporting.
- **Right not to be subject to automated decision-making (Article 22)** —
  Tides does not make any automated decisions with legal or significant
  effects on you. Insights are informational, not decisional.

You also have the **right to lodge a complaint** with a supervisory
authority. The AEPD is ours; you may also lodge a complaint with the
supervisory authority in your country of residence.

### 7.1 If you are in Brazil (LGPD)

Brazil's **Lei Geral de Proteção de Dados (Lei 13.709/2018, "LGPD")**
gives you a set of rights mirroring GDPR, with some differences in
wording. In particular, under Article 18 LGPD you have the right to:

- Confirm whether we process your data.
- Access your data.
- Correct incomplete, inaccurate, or outdated data.
- Anonymise, block, or delete data that is unnecessary, excessive, or
  processed in violation of LGPD.
- Port your data to another service provider.
- Delete data processed under your consent.
- Be informed of the public and private entities with which we have
  shared your data (see **Section 6**).
- Be informed of the possibility of refusing consent and of the
  consequences of refusal.
- Revoke your consent.

The Brazilian data-protection authority is the **Autoridade Nacional de
Proteção de Dados (ANPD)** — [www.gov.br/anpd](https://www.gov.br/anpd).

### 7.2 If you are in California (CCPA / CPRA)

Tides does not meet the revenue or volume thresholds that make us a
"business" subject to the California Consumer Privacy Act ("CCPA") /
California Privacy Rights Act ("CPRA"). However, as a matter of
transparency: **we do not sell or share your personal information** as
those terms are defined under the CCPA, and we do not engage in
cross-context behavioural advertising.

---

## 8. How to exercise your rights

For the rights we have wired into the app itself:

- **Export my data** — Settings → Your data → _Export my data_. Produces
  a JSON file containing your account profile, all your mood entries,
  weather snapshots, sky context, and insights. The file goes through
  the system share sheet so you can save it where you like. **The export
  is unencrypted; anyone with the file can read your entries. Store it
  somewhere you trust.**
- **Delete my account** — Settings → Your data → _Delete my account_.
  Your account is removed from the live database immediately; backups
  rotate out within 30 days.

For everything else (objecting to crash reporting, asking us to correct
something, asking us to restrict processing, lodging a question, etc.):

- Write to `tiopioli89@gmail.com`. Please put "Privacy request" in the
  subject line; please include the email address associated with your
  Tides account.

We aim to respond within one month of receiving a request, as required
by Article 12(3) GDPR. If your request is complex, we may extend that
period by a further two months and will tell you why.

If we cannot verify that the request is coming from the account holder,
we may ask you to confirm from the email address associated with your
account.

---

## 9. Security

We take reasonable technical and organisational measures to protect your
data:

- **Transport.** All traffic between the Tides app, the Tides server,
  and our sub-processors is over HTTPS / TLS.
- **At rest.** The Postgres database is encrypted at rest by Railway.
  Refresh tokens are stored as one-way hashes; the plaintext token is
  never persisted server-side.
- **Access.** Only Tiago Pinheiro has administrative access to the
  database. Sub-processor consoles (Sentry, Google Cloud, Railway, OpenAI)
  are protected by two-factor authentication.
- **Secrets.** On the device, your auth tokens are kept in the Android
  Keystore via `expo-secure-store`. The Android manifest blocks
  external-storage permissions so the app cannot accidentally write
  data to a shared location.

No system is one hundred percent secure. If we ever become aware of a
data breach that is likely to result in a risk to your rights and
freedoms, we will notify the AEPD within 72 hours as required by Article
33 GDPR, and we will notify you directly without undue delay as required
by Article 34 GDPR.

---

## 10. Children

Tides is **not directed at children under the age of 13**. The minimum
age to use Tides is **13 years old** (the international floor under
Article 8 GDPR for information-society services that rely on consent,
and the floor that LGPD applies in Brazil).

Spain's LOPDGDD raises the consent age for information-society services
to **14 years old**. The minimum age in Tides is locked at 13; for
Spanish residents aged 13, parental or guardian consent applies as the
LOPDGDD-compliant route. If you are 13 and resident in Spain, you (or
your guardian on your behalf) may be asked to confirm that consent.

If you are a parent or guardian and you believe we have collected data
from a child under 13, write to `tiopioli89@gmail.com` and we will
delete it.

The onboarding date-of-birth field is the gate. We do not knowingly
collect data from users below the configured minimum age.

---

## 11. Cross-border transfers

Your data may be processed outside the European Economic Area, depending
on the sub-processors named in **Section 6**:

- **Google LLC** (Sign-In) — United States, under the EU–US Data Privacy
  Framework.
- **OpenAI** (insight generation) — United States, under SCCs.
- **Railway** (server + database) — European Union (`eu-west`); no
  transfer outside the EEA.
- **Sentry** — European Union (Frankfurt); no transfer outside the EEA.
- **Open-Meteo** — European Union; no transfer outside the EEA.

You can ask for a copy of the relevant transfer mechanism by writing to
`tiopioli89@gmail.com`.

---

## 12. Changes to this policy

The **last updated** date is at the top of this document.

When we change this policy in a way that affects what we collect, who
we share it with, or what your rights are, we will:

1. Update the **last updated** date.
2. Show a calm notice in the app the next time you open it, summarising
   what changed.
3. Give you the option to delete your account before any change takes
   effect, if the change increases what we process about you.

Editorial changes (typo fixes, wording clarifications that do not change
the substance) will be made without notice.

---

## 13. Contact

- **Privacy questions:** `tiopioli89@gmail.com`
- **Controller:** Tiago Oliver Pinheiro Oliveira, Spain
- **Postal address:** Carrer Provença 60, 08901 Hospitalet de Llobregat,
  Barcelona, Spain
- **Supervisory authority:** [AEPD](https://www.aepd.es), C/ Jorge Juan, 6,
  28001 Madrid, Spain

---

## 14. A short glossary

- **Personal data.** Any information that identifies you, or could
  identify you when combined with other data. Your email is personal
  data. Your mood entry is personal data.
- **Controller.** The party that decides why and how personal data is
  processed. For Tides, that is Tiago Oliver Pinheiro Oliveira.
- **Processor / sub-processor.** A party that processes personal data
  on the controller's behalf, under the controller's instructions.
  Google, Railway, Sentry, OpenAI, and Open-Meteo are the sub-processors
  for Tides.
- **Lawful basis.** The legal ground under Article 6 GDPR that justifies
  a given processing activity. The three we rely on are: consent
  (Art. 6(1)(a)), performance of a contract (Art. 6(1)(b)), and
  legitimate interest (Art. 6(1)(f)).
- **Data subject rights.** The rights set out in Articles 15–22 GDPR.
  See **Section 7**.
