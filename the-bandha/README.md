# The Bandha Hotel & Suites: Book Direct landing page

A single-page, paid-social landing page for [The Bandha Hotel & Suites](https://thebandha.com) in Legian, Bali. Its job is to turn ad traffic into direct bookings: every call to action sends visitors to the PMG booking engine with UTM tags attached.

**Live preview:** https://moveaheadmedia.github.io/pmg-hotels/the-bandha/

Built by Move Ahead Media. Contact: Josh Tinker (josh.tinker@moveaheadmedia.com.au).

## What's in this folder

| File | Purpose |
|---|---|
| `index.html` | The whole page in one file. Plain HTML, CSS and vanilla JS. No build step, no dependencies. |
| `favicon.ico`, `favicon.png` | The Bandha gold crest favicon. |
| `DEVELOPER-HANDOFF.md` | Implementation notes, settings, hosting options and the pre-launch checklist. |
| `the-bandha-brand-ci.md` | Brand CI: logo, colour tokens, typography, UI and voice rules. |

## Running it locally

Open `index.html` in a browser. There is nothing to install.

The page loads Google Fonts (Cinzel and Open Sans), a Google Maps embed and images hotlinked from `cms.thebandha.com`, so it needs an internet connection to render fully.

## Configuring the page

Search `index.html` for `PAGE SETTINGS`. The settings block controls the booking URL, UTM tags, the IDR to AUD rate shown under prices, and the offer end date for the countdown:

```js
var BOOKING_URL='https://reservation.pmgbali.com/';
var UTM={utm_source:'MAM',utm_medium:'social',utm_campaign:'the_bandha'};
var AUD_PER_IDR=12400;   // approx. AUD shown under every IDR price
var OFFER_END='';        // e.g. '2026-10-31T23:59:00+08:00'; empty = countdown hidden
```

## Deployment

The `main` branch of the PMG Hotels repo is published automatically with GitHub Pages from the repo root, so this folder is served at `/the-bandha/`. Push to `main` and the live preview updates within about a minute.

For production, see the implementation options in `DEVELOPER-HANDOFF.md`: either host the file as-is at a clean URL on thebandha.com, or rebuild it as a page in the existing site stack.

## Before launch

Work through the checklist in `DEVELOPER-HANDOFF.md`. The main items are tracking (GA4, Meta pixel, cross-domain to the booking engine), self-hosting images, replacing placeholder reviews, confirming prices and offers with the hotel, and cross-browser QA.
