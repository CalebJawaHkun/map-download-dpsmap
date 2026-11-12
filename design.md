# DPS Map — Design Theme

## Scope and method

This reference describes the shared visual system observed on the [homepage](https://dpsmap.com/) and the first three destinations after Home in its primary navigation: [Maps](https://dpsmap.com/myanmar/), [GIS Services](https://dpsmap.com/gis/), and [Industrial Zones](https://dpsmap.com/industrial/). Observations were made on 12 November 2026 using page content, browser views, and the shared stylesheet at [`/style.css?v=27`](https://dpsmap.com/style.css?v=27). Exact values below are taken from the stylesheet when available; descriptions of imagery and page composition are visual observations.

The site has a consistent identity—cartographic imagery, blue-led color, compact uppercase labels, rounded cards, and a shared navigation/footer—while page-specific hero and content styles are not completely uniform. Treat the common tokens as the baseline, not a guarantee that every page uses the same component rules.

## Design summary

- **Personality:** precise, practical, and data-led, with local expertise presented through maps, surveying, and GIS imagery.
- **Primary visual cue:** saturated blue and navy surfaces paired with white text, often overlaid with map imagery or a subtle grid.
- **Content rhythm:** clear hero followed by spacious, centered sections; content alternates between white and pale neutral backgrounds, with information organized into cards, lists, image galleries, and calls to action.
- **Primary action style:** bold, rounded rectangular buttons. On blue heroes, a white filled action is commonly paired with a transparent white-outline action.

## Color palette

The shared stylesheet defines these core tokens:

| Role | Token / value | Typical use |
|---|---|---|
| Primary blue | `--primary-blue: #1e40af` (also `--blue`, `--navy`) | Brand, links, headings, primary actions |
| Secondary blue | `--secondary-blue: #3b82f6` | Accents, footer heading rules |
| Bright blue | `--blue-bright: #2f7ee6` | Supporting emphasis |
| Pale blue | `--sky: #eaf3ff` | Soft blue surfaces |
| Main ink | `--ink: #172033` | Body text on light backgrounds |
| Deep ink | `--deep: #0f172a` | Strong text emphasis |
| Muted text | `--muted: #64748b` | Supporting copy |
| Border | `--line: #dce3ec` | Card, control, and divider borders |
| Surface | `--surface: #f6f8fb` | Alternate sections and pale panels |
| Soft surface | `--soft: #f8fafc` | Light section backgrounds |
| White / black | `#ffffff` / `#000000` | Base surfaces and announcement strip |
| Gold | `--gold: #f59e0b` | Small eyebrow/label accent |
| Amber | `--amber: #aa6500` | Supporting warm accent |

The site footer uses a distinct dark navy (`#08182d`) with muted blue-gray text (`#b9c6d8`). The homepage and detail-page heroes use dark-to-bright blue gradients; the map-oriented heroes also use low-opacity map imagery. Some pages have their own hero-specific CSS, so the exact gradient and background treatment can vary.

## Typography

- **English:** Inter, with weights 400, 500, 600, 700, and 800 loaded from Google Fonts. The fallback stack is system sans-serif (including `-apple-system`, Segoe UI, Roboto, Helvetica Neue, and Arial).
- **Myanmar:** Noto Sans Myanmar, weights 400–700, with Myanmar Text and system sans-serif fallbacks. Myanmar-language content uses increased line-height for readability.
- **Base text:** 15px (`0.9375rem`) with a 1.6 line-height and antialiased rendering. The Myanmar-language body line-height is 1.85.
- **Headings:** bold, compact sans-serif. Section titles use responsive/clamped sizing in the shared styles. Hero headline sizes and letter spacing differ somewhat between page-specific styles.
- **Eyebrows / section labels:** small (about 12.5px), bold, uppercase, and letter-spaced; the shared eyebrow treatment adds a short gold horizontal rule.
- **Supporting copy:** generally muted gray-blue on white and pale blue on dark heroes, with comfortable line spacing and a constrained reading width.

## Layout and reusable components

- **Content width:** shared `.container` is capped at 1180px, with 16px side gutters (`width: min(1180px, calc(100% - 32px))`).
- **Sections:** substantial vertical spacing (the shared `.section` uses `4.5rem`); light alternate surfaces use `#f8fafc`.
- **Cards:** white surfaces with fine gray-blue borders, restrained shadows, and rounded corners. Shared radius tokens are 8px, 14px, and 20px; page-specific cards may use nearby values.
- **Actions:** shared buttons use bold 15px text, rounded corners (about 9px), and a subtle upward hover movement. Common variants include blue-filled, white-filled, and white-outline styles.
- **Imagery:** maps, zone diagrams, survey photography, and GIS outputs are prominent content rather than decoration alone. Images are responsive and often presented in rounded, bordered frames.
- **Floating contact action:** a fixed purple Viber/contact pill sits near the lower-right corner. At widths of 600px and below, its text is hidden and the control becomes a circular icon button.
- **Accessibility cues:** pages expose a skip-to-content link and labeled primary navigation; the mobile menu uses an expanded/collapsed button state.

## Page patterns and differences

### Homepage

The homepage opens with a two-column cartographic hero: a short “Mapping Myanmar since 1995” eyebrow, large white value-proposition headline and supporting text on the left, and a framed Myanmar map image on the right. Two contrasting actions lead to map exploration and downloads. The hero uses a dark-blue overlay over a map photograph. A compact facts band follows, then service cards, featured maps, region links, and a company introduction. Its sections balance image-led content with quick-scan metrics and linked cards.

### Maps (`/myanmar/`)

This page uses a map-textured blue hero with a “Precise cartography since 1995” label, a white headline and explanatory copy, a prominent download action, and a centered map image. The body continues into a download/request form and collections for state/region and city maps. English and Myanmar content are both present, making the Myanmar font and extra line-height relevant.

### GIS Services (`/gis/`)

The GIS page opens with a “Geospatial Solutions” eyebrow and large headline on a dark-to-blue hero with a subtle grid pattern. Two actions sit below the introductory copy, followed by a large framed surveying/drone image. The rest of the page is more editorial and technical: experience/history, capability and data-layer lists, a visual outputs gallery, coverage imagery, and a final contact call to action. It uses white bordered information panels and responsive image grids.

### Industrial Zones (`/industrial/`)

This page leads with a broad blue hero, a compact “Our Products” label, a headline and longer description, and paired actions. Below it, the design switches to a white product/catalogue layout: centered blue section headings, muted explanatory text, bordered product cards for map formats, and an industrial-zone index/preview area. Compared with the homepage and GIS page, its purchase/reference content is more catalogue-like and card-dense.

## Header & Footer

### Header

The shared header has two stacked parts:

1. **Announcement strip:** a black, full-width band with compact bold yellow promotional copy that scrolls horizontally. Its message is campaign content and can change; it is not part of the stable design tokens.
2. **Primary navigation:** a white, sticky header with a subtle lower border and translucent/blurred treatment. The desktop row uses the DPS Map logo and wordmark/tagline (“Precision Cartography”) on the left, navigation links through the center, and utility controls at the right. The logo mark is approximately 44px square in the shared stylesheet. The navigation uses small medium-weight dark-gray text; the current/hovered item turns blue and becomes slightly heavier.

The primary navigation order observed is **Home, Maps, GIS Services, Industrial Zones, Downloads, About Us**. Search and an English/Myanmar language switcher are also available. At tablet/mobile widths (1060px and below), the horizontal links collapse behind a bordered hamburger button; opening it reveals a white dropdown panel below the header, with Search at the top and the same page links beneath. The language controls remain in the header. The menu’s expanded state switches the hamburger icon to a close icon.

### Footer

The footer is a full-width deep-navy block (`#08182d`) with muted blue-gray text, generous top padding, and multiple link groups. It begins with DPS Map identity/description and then organizes site links into grouped columns, including:

- Main pages and company links
- Myanmar, state/region, city, and tourist map destinations
- Map/GIS resources and services
- Products and downloads
- A distinct contact panel with address, telephone, and email links

Group headings are white, bold, and underlined by a short blue accent rule above a fine divider. Links are smaller and muted, turning white on hover. The contact panel has a subtle outlined, rounded surface. A final thin divider separates the bottom line of copyright/developer information from legal links such as Terms & Conditions and Privacy Policy.

Responsive footer behavior is explicit in the shared CSS: at 1060px and below, its main groups stack into one column and the two footer sides separate with a horizontal rule; below 760px, link groups form two columns; at 420px and below they become single-column, the contact details stack, and the legal/copyright row becomes vertical.

## Responsive behavior

- At 1060px and below, the primary nav changes to a menu button and collapsible dropdown; desktop search is moved into the menu.
- The shared header reduces from a 74px minimum height to 66px at the tablet/mobile breakpoint, then tightens its padding and logo at 640px and below.
- Content grids and paired hero/content layouts collapse into a single column at page-specific breakpoints (commonly around 900px in the observed detail-page styles). Gallery and catalogue grids reduce columns at narrower widths.
- At 420px and below, the header wordmark text is hidden, leaving the logo mark; footer columns and contact links stack vertically.
- The browser view at a narrow/tablet-sized viewport showed the menu-button header, stacked hero text and imagery, and the floating contact action. Exact small-screen behavior can vary slightly by page because each page has additional responsive styles.

## Source pages

- [Homepage](https://dpsmap.com/)
- [Maps](https://dpsmap.com/myanmar/)
- [GIS Services](https://dpsmap.com/gis/)
- [Industrial Zones](https://dpsmap.com/industrial/)
- [Shared stylesheet](https://dpsmap.com/style.css?v=27)
