# Project Status — `map-download-dpsmap`

> Last updated: 2026-11-26

## 1. Current Phase & Active Goal

* **Active Phase:** Phase 1 — Mobile-First Black-and-White Skeletal Replica (UI Flow Complete; ready for Phase 2 merge)
* **Current Goal:** Review Phase 1 skeletal build and prepare Phase 2 visual merge with `design.md`.
* **Key Source Files:**
  * Wireframes: `references/DPS New Map-download.png`, `references/Map Image Viewer Drawer.png`, `references/Free Download Form.png`, `references/Paid Download Form.png`
  * Theme reference (Phase 2): `design.md`
  * Active page shell: `index.html`
  * Map assets: `assets/` (`maps/`, `regions/`, `districts/`, `townships/`, `cities/`, `payment/`)

---

## 2. Phase & Component Checklist

### Phase 0 — Site Shell
- [x] `[DONE]` Build responsive Header, Announcement Bar, Navigation Menu, Bilingual Switcher (`မြန်မာ | EN`), Footer, and `.viber-float` in `index.html`.
- [x] `[DONE]` Document `dpsmap.com` visual tokens and typography in `design.md`.

### Phase 1 — B&W Mobile-First Skeletal Replica
- [x] `[DONE]` Audit `references/*.png`, `assets/`, and `index.html` using `modern-web-guidance`.
- [x] `[DONE]` Complete `/grill-me` specification & draft Phase 1 Implementation Plan.
- [x] `[DONE]` Add `AGENTS.md` and `STATUS.md` for project tracking.
- [x] `[DONE]` Generate curated & deduplicated `maps-data.js` (`window.DPS_MAPS`) from `assets/`.
- [x] `[DONE]` Build `<main>` B&W wireframe sections in `index.html` (Hero, 3-up Popular Maps with images, `<search>` results grid, single Myanmar Map with `Eng | Myan` toggle, collapsible 4-col text-only State/Region & District/Township/City grids + `Filter Region` + pagination).
- [x] `[DONE]` Build bottom slide-in Map Image Viewer Drawer (`v`/`^` toggle between Drawer Opened and Drawer Closed bar, `X` dismiss, `Overview | Detail` `_` crop toggle, zoom controls, `.viber-float` auto-hide).
- [x] `[DONE]` Build Free & Paid Download Forms (`<-` Back, `X` Close, `<select>` placeholders, live mock MMK `Calculated Price`, `:user-invalid` + `aria-invalid` sync, in-drawer `"Request Received"` confirmation state).
- [x] `[DONE]` Verify asset path integrity and test all flows at `320px` and `375px` mobile viewports.

### Phase 2 — Design System Merge (`design.md`)
- [ ] `[TODO]` Replace B&W wireframe styling with `design.md` palette (`#1e40af`, `#08182d`, `#f6f8fb`, `#dce3ec`), Inter + Noto Sans Myanmar typography, and cartographic hero treatments.

### Phase 3 — Delivery & Payment Integration
- [ ] `[TODO]` Wire Free Download submission to actual file delivery / verified PDF link.
- [ ] `[TODO]` Wire Paid Download submission to `assets/payment/kpay-qr.png` payment step, real MMK pricing matrix, and backend order endpoint.

---

## 3. Locked Design Decisions

Decisions agreed during `/grill-me` (do not override without team confirmation):

1. **Host & Framing:** Insert `<main>` directly into `index.html` keeping its existing header/footer; confine `<main>` and its overlays to a centered `~430px` mobile column without wider desktop accommodations.
2. **Catalog Manifest:** Use a curated static `maps-data.js` (`window.DPS_MAPS`) so `index.html` works over both `file://` and `http://`. Pair `<name>.<ext>` with `<name>_.<ext>` detail crops; exclude `desktop.ini`, `- Copy` duplicates, and unidentifiable hash files; map flat `districts/` entries to parent `regionKey`s; keep `yangon-overview` and `shan-east/north/south` selectable.
3. **Popular Maps & Myanmar Map:**
   - `Popular Maps` renders 3 cards across (`Yangon`, `Ayeyarwady`, `Bago`) with their respective images.
   - `Myanmar Map` renders **only one** image card; the `Map Language: Eng | Myan` toggle sits beside the `Myanmar Map` section and swaps only `assets/maps/myanmar-english.jpg` / `assets/maps/myanmar-burmese.jpg`.
4. **Column Grids & Search:**
   - `State & Regional Maps` and `Districts, Townships, Towns/Cities` render **4-column text-only boxes without images**, strictly matching the wireframe column counts, with flexible heights (`min-block-size`) so text wraps without clipping.
   - `Explore Maps` search displays a dedicated results grid directly below the search bar across all categories (English + Myanmar) while keeping browse sections intact below.
   - Both accordions start open; `Filter Region` defaults to `All Regions` (with all States/Regions available) across Districts, Townships, and Cities, paginated at 12 cards per page (`3 × 4`).
5. **Map Image Viewer Drawer:** Slides in from the bottom; `v` and `^` alternate between **Drawer Opened** and **Drawer Closed** (collapsed bottom bar); `X` dismisses completely; `.viber-float` hides while the drawer is active; `Overview | Detail` toggle + zoom controls appear when a paired `*_` crop exists.
6. **Forms & Submission (Phase 1 Scope):** Use `<select>` dropdowns with generic placeholders (`Option 1`–`Option 3`) and mock MMK pricing (`10,000` / `20,000` MMK); stack 1-column on `<=360px` (2-column rows up to `430px`); on valid submit, show an in-drawer `"Request Received"` confirmation state without file download or `kpay-qr.png` yet.

---

## 4. Change Log

| Date | Contributor / Agent | Summary | Files Touched |
|---|---|---|---|
| 2026-11-26 | Antigravity (Main Session) | Implemented Phase 1 B&W mobile-first skeletal replica (`maps-data.js` + `<main>`, bottom drawer, Free/Paid forms in `index.html`), fixed `320px` `body` min-width overflow, and verified all interactive flows in browser at `320px` and `375px`. | `maps-data.js`, `index.html`, `STATUS.md` |
| 2026-11-26 | Antigravity (Side Session) | Created `AGENTS.md` and `STATUS.md` with project rules, phase checklist, and locked `/grill-me` decisions. | `AGENTS.md`, `STATUS.md` |
| 2026-11-26 | Antigravity (Main Session) | Audited `references/*.png` and `assets/` with `modern-web-guidance`; completed `/grill-me` alignment and drafted Phase 1 Implementation Plan. | *(Plan artifact)* |
| 2026-11-26 | Team (per `index.html` / `design.md`) | Created responsive Header/Footer shell in `index.html` and documented `dpsmap.com` design tokens in `design.md`. | `index.html`, `design.md` |
