# Project Status — `map-download-dpsmap`

> Last updated: 2026-11-26

## 1. Current Phase

* **Active Phase:** Phase 1 Complete — Ready for Phase 2 (`design.md` Visual Merge)
* **Key Reference Files:**
  * Wireframes: `references/DPS New Map-download.png`, `references/Map Image Viewer Drawer.png`, `references/Free Download Form.png`, `references/Paid Download Form.png`
  * Theme reference (Phase 2): `design.md`
  * Active page & catalog: `index.html`, `maps-data.js`, `assets/`
  * Status tracking workflow: `.agents/skills/status-tracking/SKILL.md`

---

## 2. Locked Design Decisions

Decisions agreed during `/grill-me` (do not override without team confirmation):

1. **Host & Framing:** Insert `<main>` directly into `index.html` keeping its existing header/footer; confine `<main>` and its overlays to a centered `480px` mobile column without wider desktop accommodations.
2. **Catalog Manifest:** Use a curated static `maps-data.js` (`window.DPS_MAPS`) so `index.html` works over both `file://` and `http://`. Pair `<name>.<ext>` with `<name>_.<ext>` detail crops; exclude `desktop.ini`, `- Copy` duplicates, and unidentifiable hash files; map flat `districts/` entries to parent `regionKey`s; keep `yangon-overview` and `shan-east/north/south` selectable.
3. **Popular Maps & Myanmar Map:**
   - `Popular Maps` renders 3 cards across (`Yangon`, `Ayeyarwady`, `Bago`) with their respective images.
   - `Myanmar Map` renders **only one** image card; the `Map Language: Eng | Myan` toggle sits beside the `Myanmar Map` section and swaps only `assets/maps/myanmar-english.jpg` / `assets/maps/myanmar-burmese.jpg`.
4. **Column Grids & Search:**
   - `State & Regional Maps` and `Districts, Townships, Towns/Cities` render **4-column text-only boxes without images**, strictly matching the wireframe column counts, with taller `min-block-size: 62px` and contained `fit-content` pill strips so text wraps without clipping.
   - `Explore Maps` search displays a dedicated results grid directly below the search bar across all categories (English + Myanmar) while keeping browse sections intact below.
   - Both accordions start open; `Filter Region` defaults to `All Regions` (with all States/Regions available) across Districts, Townships, and Cities, paginated at 12 cards per page (`3 × 4`).
5. **Map Image Viewer Drawer:** Slides in from the bottom (`480px` max width); `v` and `^` are centered in a 3-column header grid and alternate between **Drawer Opened** (`clamp(300px, 50dvh, 620px)` preview canvas) and **Drawer Closed** (collapsed bottom bar); `X` dismisses completely; `.viber-float` hides while the drawer is active; `Overview | Detail` toggle + zoom controls appear when a paired `*_` crop exists.
6. **Forms & Submission (Phase 1 Scope):** Use `<select>` dropdowns with generic placeholders (`Option 1`–`Option 3`) and mock MMK pricing (`10,000` / `20,000` MMK); stack 1-column on `<=360px` (2-column rows up to `480px`); on valid submit, show an in-drawer `"Request Received"` confirmation state without file download or `kpay-qr.png` yet.
7. **Status Tracking Format:** `STATUS.md` tracks **completed work only** (no checklists or future TODO lists). Each completed task logs its own entry under `### Uncommitted (since <HEAD>)` with `Added`, `Modified`, and `Deleted` records until the next commit, rolling over into `### Commit <hash> — <subject> (<date>)` once committed.

---

## 3. Completed Work

### Uncommitted (since `c527d10`)

#### 2026-11-26 16:53 — Refine Mobile Column Width, Box Height, Pill Containment & Drawer Sizing (`Antigravity`)
Widened the mobile column and drawer to `480px`, contained the `Regions | States` pill strip to its content width, increased 4-column box heights to `62px`, centered the drawer chevron toggle via a 3-column grid, and expanded the map preview canvas to `50dvh` (`clamp(300px, 50dvh, 620px)`), verified across `1024×900`, `480×840`, and `320×568` viewports.
- **Added:**
  - None
- **Modified:**
  - `index.html` — Updated `.wf-main` and `.wf-drawer` to `480px`, `.wf-segmented` to `fit-content`, `.wf-box-btn` to `min-block-size: 62px`, `.wf-drawer-bar--viewer` to a 3-column grid centering `#viewer-toggle-btn`, and `.wf-preview-canvas` to `clamp(300px, 50dvh, 620px)` with `data-zoomed` fit-to-canvas scaling.
  - `STATUS.md` — Synced Locked Design Decisions and logged this completion entry.
- **Deleted:**
  - None

#### 2026-11-26 16:45 — Refactor Status Tracking to Completion-Only Commit Ledger (`Antigravity`)
Replaced the checklist-driven workflow with a completion-only, commit-scoped tracking skill and ledger format recording Added, Modified, and Deleted files between commits.
- **Added:**
  - `.agents/skills/status-tracking/SKILL.md` — Workspace skill defining git-diff inspection, entry formatting, and commit-cycle rollover rules.
- **Modified:**
  - `AGENTS.md` — Updated Section 1 to reference `.agents/skills/status-tracking/SKILL.md` and enforce completion-only commit-cycle logging.
  - `STATUS.md` — Removed checklists and Change Log table; structured into Current Phase, Locked Design Decisions, and Completed Work seeded from commit history.
- **Deleted:**
  - None

---

### Commit `c527d10` — `mapdownload-initial-UI` (2026-11-26)

#### 2026-11-26 — Phase 1 B&W Mobile-First Skeletal Replica (`Antigravity / Team`)
Built and browser-verified the Phase 1 black-and-white wireframe UI flow inside `index.html` backed by the curated `assets/` catalog in `maps-data.js`, alongside project governance docs.
- **Added:**
  - `maps-data.js` — Curated `window.DPS_MAPS` manifest indexing `assets/` with `_` detail-crop pairing and region tags.
  - `assets/` — Map image catalog (`maps/`, `regions/`, `districts/`, `townships/`, `cities/`) and `payment/kpay-qr.png`.
  - `references/` — Four wireframe PNG references (`DPS New Map-download.png`, `Map Image Viewer Drawer.png`, `Free Download Form.png`, `Paid Download Form.png`).
  - `AGENTS.md`, `STATUS.md` — Initial project rules and status tracking documents.
- **Modified:**
  - `index.html` — Implemented `<main>` B&W wireframe sections (Hero, 3-up Popular Maps, `<search>`, single Myanmar Map + `Eng | Myan` toggle, 4-column text-only State/Region & District/Township/City grids, pagination), bottom slide-in Map Image Viewer Drawer (`v`/`^`/`X`, `Overview | Detail`, zoom), and Free/Paid Download Forms with `:user-invalid` validation and `"Request Received"` state.
- **Deleted:**
  - None

---

### Commit `1e96bf7` — `Merge pull request #8 from CalebJawaHkun/kyaw-soe-min` (2026-11-12)

#### 2026-11-12 — Site Footer & Viber Float Shell (`Team`)
Completed the shared footer columns, contact card, legal links, and floating `.viber-float` contact button in `index.html`.
- **Added:**
  - None
- **Modified:**
  - `index.html` — Added responsive deep-navy `.site-footer` and `.viber-float` shell.
- **Deleted:**
  - None

---

### Commit `254986e` — `header_commit` (2026-11-12)

#### 2026-11-12 — Site Header & Bilingual Navigation Shell (`Team`)
Implemented the announcement strip, sticky navigation bar, search bar, mobile drawer toggle, and `မြန်မာ | EN` UI language switcher in `index.html`.
- **Added:**
  - None
- **Modified:**
  - `index.html` — Built `.announcement-bar` and `.site-header` navigation shell.
- **Deleted:**
  - None
