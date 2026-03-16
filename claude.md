# Fourth International Declaration — Antifascist Forum, Brazil

Multi-page website presenting declarations of the Fourth International. Each declaration is a self-contained HTML file.

## Project structure

- `index.html` — The Antifascist Forum (Brazil 2026) declaration
- Future declarations get their own HTML files (e.g., `declaration-2025-climate.html`)

## Design

- Dark theme with light mode via `prefers-color-scheme`
- Strong red and black palette; CSS custom properties for all theme colors
- Playfair Display (headings) + Inter (body) + Noto Sans Arabic (RTL)
- Scroll-triggered fade-in animations, animated diagonal stripe texture, red scroll progress bar
- Fourth International logo as hero background graphic and closing mark

## Multilingual

Five languages: English (default), Portuguese, French, Spanish, Arabic. Translations live in a JS `translations` object keyed by `data-i18n` attributes. Arabic triggers RTL layout via `dir="rtl"` on `<html>`.

When editing text, update both the HTML element and the corresponding key in the `translations` object for all four languages.

## Print

The print button calls `window.print()`. A `@media print` block strips dark backgrounds, animations, and navigation, producing a clean black-on-white layout suitable for PDF export. To suppress browser-generated headers/footers (URL, date), uncheck "Headers and footers" in the browser print dialog.

## Key conventions

- No build tools, bundlers, or dependencies — everything is in the single HTML file
- All theme colors use CSS custom properties defined in `:root` and overridden in the `prefers-color-scheme: light` media query
- Section dividers use the `.star-ornament` class (star SVG flanked by gradient lines)
- The English text matches the formatting of the canonical docx source (paragraph breaks, bold, italics)

## Sidebar (declarations index)

A collapsible sidebar lists all declarations with title and date. It is triggered by a hamburger icon in the lang-bar and slides in from the left (right in RTL/Arabic).

- The `declarations` JS array and sidebar rendering code are **duplicated in every HTML file** (no shared JS files)
- **When adding a new declaration**, you must update the `declarations` array in every existing HTML file and create the new file with the same array
- Each entry has: `title` (object with keys for each language), `date`, `url` (relative path to the HTML file), and `current` (boolean, true only in that declaration's own file)
- Placeholder entries use `url: "#"` and are styled muted
