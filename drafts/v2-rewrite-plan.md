# Rewriting the help center for v2

**Decided 2026-09-18 (David):** the help center documents **v2**, not v1.

This file is a working plan, not a published page — `.mintignore` excludes
`drafts/`. Delete it when the rewrite is finished.

## What was here before

53 MDX pages, written May 2026 against **v1's** screens. 12 of them were
Mintlify starter-template leftovers (`analytics/`, `integrations/`,
`platform/` — "CRM connectors", "Configure webhooks") that were never in the
navigation; they and the Mac `.DS_Store` / `._*` junk files were deleted at the
start of this rewrite. That leaves **41 real pages**, and essentially all of
them describe screens, fields and rules that v2 does not have.

## The five things that break the most pages

Every page has to be re-read against these, because a page can be right about
the feature and wrong about the rule:

1. **Navigation.** v1 had a nine-item sidebar (Dashboard, Counselees, Schedule,
   Sessions, Notes, Forms, Resources, Book Library, Settings). v2 has **six
   workspaces** — Today, Counselees, Session, Schedule, Practice and, for
   counselees, My care — with depth in drawers over the workspace, and a **⌘K
   command palette** for anything at all. No page may send a reader to a
   sidebar item that no longer exists.
2. **Nothing clinical is deleted.** v1's docs offer permanent delete of
   archived counselees, deleting an appointment "instead of cancelling", and
   editing a counselee's own form answer so that "the original text is not
   preserved". v2 is archive-only: records close and reopen, notes and sessions
   are **signed, locked and corrected by addendum**, and corrections are
   permanent additions rather than overwrites.
3. **No counseling content in email, ever.** v1 emailed homework content in
   the body, attached resource files, and auto-emailed a PDF of every form
   submission to the admin inbox. v2 sends **notification-only** email — "sign
   in to view" — and everything else lives behind sign-in.
4. **Who can see what.** v1 scoped by primary/co/additional counselor fields on
   the profile. v2 scopes by **caseload**, assignments are history rows that
   close and open rather than being edited, and an org admin reading clinical
   content **must give a reason that is recorded**. Access grants open the case
   record and supervision entries only — never notes, files, sessions,
   measurements, homework, care plans, messages or prayer requests.
5. **Which clock a time is shown on.** Planning screens (Today, Schedule) draw
   on the **viewer's** clock; the clinical record draws on the **practice's**.
   Any page quoting a time has to say which, exactly as the screens do.

## Page-by-page

`REWRITE` = same subject, new text. `REPLACE` = the subject itself changed.
`NEW` = v2 feature with no page at all.

### Getting started

| Page | Verdict | Why |
|---|---|---|
| `index.mdx` | REWRITE | Card grid points at the old structure |
| `getting-started/introduction` | REWRITE | "Invitation codes" — v2 has emailed invites and a self-serve free trial at `/start` |
| `getting-started/logging-in` | REWRITE | Says two-factor is "optional but recommended". In v2 a **strong second factor is mandatory for staff** (authenticator app or a passkey), then a timezone gate, then consent documents. Passkeys can be offered in the email field. |
| `getting-started/navigating-the-app` | REPLACE | The whole sidebar table is gone. New subject: six workspaces, cards, drawers, ⌘K, switching practice and switching role |
| `getting-started/starting-a-free-trial` | NEW | Self-serve signup, what a trial is, what happens when it ends |

### Counselees

| Page | Verdict | Why |
|---|---|---|
| `counselees/adding-a-counselee` | REWRITE | No "Auto-send PDI"; the record is a **person at this practice with cases inside it**; remove permanent delete |
| `counselees/counselee-statuses` | REPLACE | v2 has cases with discharge and reopen, both stamped; permanent deletion does not exist |
| `counselees/assigning-counselors` | REWRITE | Assignment is a history row, not a profile field; caseload scoping; access grants and what they do *not* open |
| `counselees/the-intake-queue` | NEW | Enquiries, the intake queue, intake staff |

### Schedule

| Page | Verdict | Why |
|---|---|---|
| `scheduling/setting-your-availability` | REWRITE | Booking hours store a rule and a zone |
| `scheduling/creating-appointments` | REWRITE | A series stores its rule; occurrences are virtual until touched. Cancelling never deletes |
| `scheduling/time-off-blocks` | REWRITE | Blockouts are wall-time recurring |
| `scheduling/calendar-sharing` | REWRITE | Feed tokens expire, are rate-limited and revocable |
| `scheduling/appointment-reminders` | REWRITE | Practice-level reminder settings; **text reminders exist but stay switched off until carrier registration is approved** |
| `scheduling/which-clock` | NEW | Viewer's clock vs practice's clock, and why the two screens can differ |

### Sessions

| Page | Verdict | Why |
|---|---|---|
| `sessions/starting-a-session` | REWRITE | Session prep and the session surface; "Complete Session" becomes **sign** |
| `sessions/signing-and-corrections` | NEW | Sign → lock → addendum. The single most important page in the set |
| `sessions/session-modules` | REWRITE | Confirm the v2 module list against the code before writing |
| `sessions/session-templates` | REWRITE | Confirm personal vs practice scope in v2 |
| `sessions/joint-sessions` | REWRITE | Per-person boundaries hold inside a shared case |
| `sessions/follow-ups` | REWRITE | Check against v2's care plans and homework |

### Forms and intake

| Page | Verdict | Why |
|---|---|---|
| `forms/the-default-pdi` | REWRITE | No auto-send; token expiry is v2's |
| `forms/building-a-custom-form` | REWRITE | Check field types and profile mapping against v2's builder |
| `forms/sending-a-form` | REWRITE | Intake packets and tokens; expiry, rate limiting, revocation |
| `forms/reviewing-submissions` | REWRITE | **Remove "edit the answer, original not preserved"** |
| `forms/exporting-submissions` | REWRITE | **Remove the auto-emailed PDF** — that is counseling content in email |

### Resources, books, supervision

| Page | Verdict | Why |
|---|---|---|
| `resources/assigning-resources` | REWRITE | **Assignment email carries no content** — it says sign in to view |
| `resources/the-resource-library` | REWRITE | Check against v2's library |
| `resources/lessons-and-homework` | REWRITE | Same |
| `book-library/*` (3 pages) | REWRITE | Check inventory, lending and book-homework against v2 |
| `supervision/logging-supervision-hours` | REWRITE | The journal is author-owned; hours are computed, never stored |
| `supervision/acbc-progress-tracking` | REWRITE | Same |

### Portal, files, money, practice

| Page | Verdict | Why |
|---|---|---|
| `portal/counselee-overview` | REWRITE | My care: appointments, homework, documents, messages |
| `portal/inviting-counselees` | REWRITE | Invited by **email address**, never by user id; the link is written at activation |
| `portal/prayer-requests` | REWRITE | Check against v2 |
| `portal/messages` | NEW | Portal messaging |
| `files/attaching-files` | REWRITE | Drag and drop; encrypted at rest; served behind sign-in, never a public link |
| `files/sharing-files` | REWRITE | Sharing is recorded as a disclosure |
| `billing/how-billing-works` | REPLACE | v2 has named plans (some per counselor, some flat), free trials, and a read-only state when a subscription lapses |
| `billing/managing-your-subscription` | REWRITE | One subscription per practice |
| `money/charging-counselees` | NEW | Pay links, card payments, receipts, statements — none of this is in the current docs |

⚠ **Practice has THREE money cards and they are not the same thing** (confirmed
on screen 2026-09-18). **Billing** is the standard session fee this practice
charges a counselee; **Payments** is taking card payments through a connected
Stripe account; **Subscription** is what the practice pays us. The first draft
of `setting-up-your-practice` merged Billing and Subscription and had to be
fixed — the money pages must keep them apart.
| `practice/your-team` | NEW | Inviting staff, roles, removing someone, the last-admin rule |
| `practice/consent-documents` | NEW | Versioned consent, recorded server-side |
| `practice/audit-log-and-email-history` | NEW | What is recorded and how to read it |
| `practice/reports` | NEW | The reports page |
| `privacy/who-can-see-what` | NEW | The confidentiality rules in plain English, including break-glass |

**41 pages in, roughly 47 out.**

## Navigation

`docs.json` groups become: Getting started · Counselees · Schedule · Sessions ·
Forms & intake · Resources & homework · Book library · Supervision ·
Counselee portal · Files & documents · Money · Your practice · Privacy &
security.

The platform console is **not documented here** (David, 2026-09-18) — the help
center covers what a practice sees. Console notes belong in the app repo's
`docs/`.

## Two open URL questions

- `docs.json` points "Sign In" at `soulcaremanager.com/login` and "Go to App"
  at `app.soulcaremanager.com`. v2 lives at `v2.soulcaremanager.com` until
  cutover and at `soulcaremanager.com` afterwards. Pages are being written
  against the **final** domain.
- Publishing is David's call. Nothing here is pushed without it.

## House terms, as the app spells them

Match these exactly; the first draft got three of them wrong.

- **Inquiries**, not enquiries (the Practice card is `INQUIRIES`)
- **Center Admin**, **Counselor**, **Intake** are the role names on the invite
- **Complete session** → confirmed with **Complete & lock**; a locked session
  reads `Complete · locked` and offers **Add addendum**
- **Addendum — add information** / **Correction — the record was wrong**
- **My care** is the counselee's workspace

## Order of work

1. ~~Delete the template leftovers and junk files~~ (done)
2. ~~Getting started + `index.mdx` + `docs.json`~~ (done — the exemplar)
3. ~~The rule pages: signing and corrections, who can see what, which clock~~
   (done)
4. ~~Verify 1–3 against the running app~~ (done 2026-09-18 —
   `tools/exercise-docs-screens.mjs` in the app repo. Six corrections came out
   of it, the worst being Billing/Subscription above)
5. Then the feature groups, one at a time. **Photograph each surface before
   writing it** — that is where every correction in step 4 came from, not from
   reading the code.
