# Open questions for Tiago before publication

Internal working notes. Not published — this directory is excluded from
the Jekyll build (`_notes/` is underscore-prefixed; also listed under
`exclude:` in `_config.yml`).

---

## Privacy Policy

**Resolved (2026-05-20):**

- [x] **Postal address** — `Carrer Provença 60, 08901 Hospitalet de
      Llobregat, Barcelona, Spain`. Wired into **Section 1** and
      **Section 13**.
- [x] **Controller name** — `Tiago Oliver Pinheiro Oliveira`. Wired
      throughout (Sections 1, 13, 14).
- [x] **Railway region** — confirmed `eu-west` (EU). **Section 6.2**
      now states "no transfer outside the EEA"; the SCC paragraph has
      been removed; **Section 11** moves Railway out of the US-transfer
      list.
- [x] **Minimum age** — locked at **13**. **Section 10** retains the
      Spain-specific LOPDGDD 14-year note (guardian-consent route for
      Spanish residents aged 13).
- [x] **Host on a stable HTTPS URL** — published at
      `https://tiago-o-pinheiro.github.io/tides-legal/`. URL is wired
      into the mobile app constants and into the in-app Terms/Privacy
      links (`apps/mobile/src/core/constants/app.constants.ts`).
- [x] **In-app Terms/Privacy link wiring** — done; `Linking.openURL`
      replaces the old placeholder sheet in `Welcome.view.tsx` and
      `GoogleSignIn.view.tsx`.

**Still open:**

- [ ] **Lawyer review** — mandatory before public publication.
- [ ] **Translate to ES / CA / PT-BR.** Acceptable to defer to v1.1, but
      preferably by a legal translator (not the in-app psychologist).
- [ ] **Match Play Console Data Safety form** to this policy exactly.
      Draft the Data Safety answers from this document; do not draft
      them from memory. See `data-safety.md` for the draft.
- [ ] **Diff against current code reality** on the day before submission.
      Re-grep for new SDKs, new fields, new permissions.
- [ ] **Decide on a Sentry opt-out.** Until it ships, the only opt-out
      route is by email — **Section 7** describes this. An in-app toggle
      is on the v1.1 list.
- [ ] **Decide on an OpenAI opt-out.** Same as above. Users who do not
      want their reflection processed by a US sub-processor currently
      have to leave the reflection field empty.
- [ ] **Confirm OpenAI's training/retention policy** is unchanged from
      what is stated in **Section 6.4** on the day of publication.
- [ ] **Decide whether to expose per-entry deletion** in Settings (today,
      v1 only exposes full-account deletion). Section 3.2 references this.

---

## Terms of Service

**Resolved (2026-05-20):**

- [x] **Postal address** — `Carrer Provença 60, 08901 Hospitalet de
      Llobregat, Barcelona, Spain`. Wired into **Section 1** and
      **Section 14**.
- [x] **Controller name** — `Tiago Oliver Pinheiro Oliveira`. Wired
      throughout.
- [x] **Railway region** — confirmed `eu-west` (EU). The Privacy Policy
      has been updated accordingly; these Terms remain in sync.
- [x] **Minimum age** — locked at **13**. **Section 10** retains the
      Privacy Policy cross-reference for the Spain-specific LOPDGDD
      14-year note (guardian consent route for Spanish residents aged
      13).
- [x] **Liability cap** — locked at **€100** in **Section 11**, paired
      with the EU consumer-protection carve-out. Lawyer review will
      confirm whether the cap survives in a consumer-facing version or
      whether to rely solely on the carve-out.
- [x] **Host on a stable HTTPS URL** — published alongside the Privacy
      Policy at `https://tiago-o-pinheiro.github.io/tides-legal/terms.html`.
- [x] **Wire the in-app Terms link** — done; the placeholder at
      `apps/mobile/src/modules/onboarding/components/terms-placeholder-sheet/`
      has been deleted and replaced with direct `Linking.openURL` calls.

**Still open:**

- [ ] **Lawyer review** — mandatory before public publication.
- [ ] **Translate to ES / CA / PT-BR.** Acceptable to defer to v1.1, by
      a legal translator.
- [ ] **Diff against current code reality** on the day before
      submission. If Tides has added a paid tier, scraping protections,
      a sharing surface, or any feature outside the v1 scope, these
      terms must be updated first.
