# The Bandha: Book Direct Landing Page (developer handoff)

**Goal:** get more direct bookings. Paid social traffic lands here, and every CTA sends visitors to the PMG booking engine with UTM tags.
**Contact:** Josh Tinker, Move Ahead Media (josh.tinker@moveaheadmedia.com.au)

## Files
| File | What it is |
|---|---|
| `index.html` | The complete page in one file. Plain HTML, CSS and vanilla JS, with no build step or dependencies. Open it in a browser to see it. |
| `the-bandha-brand-ci.md` | Brand CI: logo, colour tokens, type, UI and voice rules. |

## How it's built
- **One file, one page.** CSS is in `<style>` and the brand tokens are CSS variables at the top of `:root`. The JS sits at the bottom of `<body>`.
- **External resources:**
  - Google Fonts: Cinzel and Open Sans
  - Google Maps embed (no API key needed)
  - Images hotlinked from `cms.thebandha.com/uploads`
- **Settings block** (search the file for `PAGE SETTINGS`):
  ```js
  var BOOKING_URL='https://reservation.pmgbali.com/';
  var UTM={utm_source:'MAM',utm_medium:'social',utm_campaign:'the_bandha'};
  var AUD_PER_IDR=12400;   // approx. AUD shown under every IDR price
  var OFFER_END='';        // e.g. '2026-10-31T23:59:00+08:00'; empty = countdown hidden
  ```
- **Booking widget:** builds `BOOKING_URL?checkin=YYYY-MM-DD&checkout=YYYY-MM-DD&rooms=1&adults=N&children=N&utm_...`. The booking engine accepts these parameters (tested).
- **All `[data-book]` links** get `BOOKING_URL + UTM` from JS. Static hrefs with UTMs are also hard-coded as a fallback for when JS doesn't run.

## Implementation options (pick one)
1. **Fastest:** host the file as-is at a clean URL, e.g. `thebandha.com/book-direct` or `offers.thebandha.com`.
2. **Native:** rebuild it as a page in the existing thebandha.com stack (Next.js front end, Strapi-style CMS at cms.thebandha.com) using the same markup and tokens. Offers and prices can then come from the CMS instead of being hard-coded.

## Must do before launch
- [ ] **Booking URL:** decide with the client whether to switch to `https://reservation.pmgbali.com/the-bandha`. The root URL also lists sister hotels, and The Magani appeared above The Bandha in testing.
- [ ] **Tracking:**
  - Add GA4/GTM and the Meta pixel.
  - Set up cross-domain measurement to `reservation.pmgbali.com`.
  - The booking engine rewrites its URL on load (it drops the `utm_` parameters and adds `mam_cid`). Make a test booking and confirm the session is attributed to MAM / social / the_bandha.
- [ ] **Images:**
  - Download them from the CMS and self-host them, as WebP in responsive sizes with `srcset`, so the page keeps working if CMS files are renamed.
  - The hero image is a large PNG. Compress it.
- [ ] **Fonts:** Trajan Pro is the brand heading font. If the client holds a web licence, self-host it; the CSS already lists it first. Otherwise Cinzel is the fallback.
- [ ] **Head tags:** add Open Graph and Twitter tags (it's a social campaign), a favicon, and a canonical URL. Use `noindex` if it's paid-traffic only.
- [ ] **Placeholder content to replace:**
  - [ ] 3 guest review quotes (search for `Verified guest review`). Use real, attributed reviews only.
  - [ ] `OFFER_END` for the 10.10 countdown, using the real end date from the hotel.
  - [ ] **Prices and offers:** confirm they're current. They were taken from thebandha.com on 14 Oct 2026.
  - [ ] **Direct vs booking-sites table:** have the hotel confirm each perk is direct-only.
  - [ ] **Redeemable Room Night copy:** confirm how the membership points work.
- [ ] **QA:**
  - [ ] Test on iOS Safari and Android Chrome, especially the date inputs.
  - [ ] Run Lighthouse (performance and accessibility).
  - [ ] Check every CTA opens the booking engine with the UTM tags.
  - [ ] Check the gallery lightbox (Esc and arrow keys), the in-page nav and the mobile sticky book bar.

## Page structure (top to bottom)
1. Promo ribbon, with the countdown when it's set
2. Sticky header
3. Hero with booking widget and trust line
4. Trust bar
5. Why book direct
6. Offers
7. Rooms
8. Gallery and lightbox
9. Experience
10. Direct vs booking sites
11. Reviews
12. Location and map
13. FAQ
14. Final CTA
15. Footer
16. Mobile sticky book bar
