# Soul Care Manager Help Center

The help center for Soul Care Manager, published by [Mintlify](https://mintlify.com)
from this repo's `main` branch. Pages are MDX files with YAML frontmatter;
navigation, redirects and the app links live in `docs.json`.

- `mint dev` previews locally; `mint broken-links` checks links.
- The app lives at `https://app.soulcaremanager.com`. The bare
  `soulcaremanager.com` is the public landing page, not the app.
- The platform console is never documented here: this covers what a practice
  and its counselees see.

## How to update it (the way it was done in 2026-09 and 2026-11)

Write every page from what the screen **says**, never from the code alone. The
first v2 draft was written from the code and the screens corrected it six
times (the worst: Practice's Billing card is what a practice charges, not what
it pays us).

1. **Photograph the app.** In the app repo (`soulcaremanager`), with the dev
   stack up and the acceptance cast seeded:

   ```
   docker compose run --rm puppeteer node tools/exercise-docs-tour.mjs
   ```

   It signs in as each role of the cast (Daniel the counselor, Ruth the
   administrator, Grace on intake, Jerome the counselee) and saves a
   screenshot and the page's words for every address a help page describes,
   plus the drawers and panels a click opens, to
   `tools/screenshots/docs-tour/`. It writes nothing. Add `opened` to rerun
   only the click-through part.
2. **Read the words, page by page,** against each help page, and rewrite what
   no longer matches. Quote the app's own labels exactly, in bold.
3. **Branch** (`fix/` or `feat/`), commit, push, and open a PR. Merging to
   `main` publishes the site.

## House style

- American English, as the app is: inquire, counselor, color, catalog. The
  app spells "cancelled" with two Ls, so the docs do too.
- Second person, active voice, short sentences. Sentence case for headings.
- **Bold** for anything on screen; *italics* for a sentence quoted from it.
- Say which clock a time is on whenever it matters (the viewer's on Today and
  Schedule, the practice's on the record and in the portal).
- Never describe deleting a clinical record, emailing counseling content, or
  editing a signed record: v2 does none of them.

## Terms, as the app spells them

- **Center Admin**, **Counselor**, **Intake** are the role names.
- **Inquiries**, never enquiries.
- **Complete session**, confirmed with **Complete & lock**; a locked session
  reads *Complete · locked* and offers **Add addendum**.
- **My care** is the counselee's portal.
- **Practice → Section → Page** names where something is, e.g.
  **Practice → Scheduling → Booking hours**.
