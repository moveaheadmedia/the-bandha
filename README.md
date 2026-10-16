# PMG Hotels: Book Direct landing pages

Paid-social landing pages for the PMG Bali hotel group. Each hotel has its own folder with a single-file page (plain HTML, CSS and vanilla JS, no build step) whose job is to turn ad traffic into direct bookings through the PMG booking engine with UTM tags attached.

**Live index:** https://moveaheadmedia.github.io/pmg-hotels/

Built by Move Ahead Media. Contact: Josh Tinker (josh.tinker@moveaheadmedia.com.au).

## Hotels

| Folder | Hotel | Live preview |
|---|---|---|
| [`the-bandha/`](the-bandha/) | The Bandha Hotel & Suites, Legian | https://moveaheadmedia.github.io/pmg-hotels/the-bandha/ |
| [`the-magani/`](the-magani/) | The Magani Hotel and Spa, Legian | https://moveaheadmedia.github.io/pmg-hotels/the-magani/ |

Each folder has its own `README.md` with the page settings and launch notes. The shared developer handoff and pre-launch checklist live in `the-bandha/DEVELOPER-HANDOFF.md`.

## Adding a hotel

1. Create a new folder named after the hotel in kebab-case, for example `the-new-hotel/`.
2. Put the page in it as `index.html`, plus any favicon files and a `README.md`.
3. Add a row to the table above and a card to the root `index.html`.
4. Push to `main`. GitHub Pages serves the folder at `/pmg-hotels/<folder>/`.

## Deployment

The `main` branch is published automatically with GitHub Pages from the repo root. Push to `main` and the live previews update within about a minute.
