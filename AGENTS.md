# AGENTS.md — DPS Map Download Project

Guidance for AI coding agents and contributors working in `map-download-dpsmap` (see `README.md` for team contributors).

## 1. Status Tracking Workflow (Mandatory)

1. **Read `STATUS.md` first** before starting any task to align with the current phase, recent completed changes, and locked design decisions.
2. **Record every completion in `STATUS.md`** by following `.agents/skills/status-tracking/SKILL.md`:
   - `STATUS.md` tracks **completed work only**—never add checklists (`- [ ]` / `- [x]`) or future TODO lists there.
   - Log each completed task as an entry under `### Uncommitted (since <HEAD>)` listing all **Added**, **Modified**, and **Deleted** items until the next commit, rolling prior uncommitted groups into `### Commit <hash> — <subject> (<date>)` when `HEAD` advances.
   - Add any newly agreed product/UX decisions to **Locked Design Decisions**.
3. **Keep `AGENTS.md` lean:** Record evolving progress and changelogs in `STATUS.md`, never here.

## 2. Project Phases & Visual Scope

* **Current Phase — Phase 1 (B&W Skeletal Replica):**
  * Build `<main>` and its interactive drawer/form flows directly inside `index.html`, preserving the existing Header, Announcement Bar, Footer, and `.viber-float` shell.
  * Style `<main>`, cards, drawer, and forms in the **black-and-white bordered wireframe style** (`references/*.png`) until Phase 1 UI flow is complete.
  * Do **not** merge `design.md` brand colors or hero styling into `<main>` until Phase 2 begins.
* **Future Phases:**
  * **Phase 2:** Merge `<main>` and overlays with `design.md` visual tokens (`#1e40af`, `#08182d`, `#f6f8fb`, Inter + Noto Sans Myanmar).
  * **Phase 3:** Connect backend submission, actual map file delivery, and KBZPay QR payment (`assets/payment/kpay-qr.png`).

## 3. Mobile-First & Layout Constraints

* **Mobile-only viewport default:** Constrain `<main>` and bottom overlays to a centered mobile column (`~430px` max width, reflowing cleanly down to `320px`) with **no wider desktop viewport accommodations** for `<main>`.
* **Never** use `overflow-x: hidden` or `clip` on `html` or `body` to mask horizontal overflow; make child layouts fit within `320px`.
* Support bilingual English and Myanmar text cleanly: avoid fixed `height` / `block-size` on text containers (use `min-block-size` and `overflow-wrap: break-word` so taller Myanmar glyphs and scaled text never clip).

## 4. Data & Asset Rules (`assets/`)

* Serve the curated map catalog from `maps-data.js` as a classic script (`window.DPS_MAPS`) so `index.html` works over both `file://` and `http://`.
* When regenerating or editing `maps-data.js` from `assets/`:
  * Pair `<name>.<ext>` overview maps with `<name>_.<ext>` zoomed detail crops (`{ overviewSrc, detailSrc }`).
  * Exclude `desktop.ini`, `- Copy` duplicates, and unidentifiable hash filenames.
  * Tag flat `assets/districts/Districts/` files with their parent `regionKey` so `Filter Region` works across Districts, Townships, and Cities.

## 5. Web Standards & Browser Support Policy

* Consult `modern-web-guidance` before implementing or refactoring HTML, CSS, or client-side JS UI patterns.
* **Browser Support:** Rely on Baseline Widely Available features by default. Adopt Baseline Newly Available features only with lightweight progressive enhancement or feature-detected fallbacks; avoid volatile single-engine APIs unless explicitly requested.
* **Forms & Accessibility:**
  * Keep inputs/selects at `font-size: max(1rem, 1em)` (`>= 16px`) to prevent iOS auto-zoom, and target `>= 44px` hit areas on touch controls.
  * Use `:user-invalid` synced with `aria-invalid` (initialize `aria-invalid="false"`) and keep submit buttons enabled.
  * Guard custom `Enter` handlers on search inputs with `event.isComposing || event.keyCode === 229` for Myanmar IME compatibility.
  * Never place headings inside `<summary>`; use a `<button aria-expanded>` inside the heading for collapsible sections.
