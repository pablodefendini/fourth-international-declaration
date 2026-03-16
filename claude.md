# Fourth International Declaration — Antifascist Forum, Brazil

Single-page website presenting the declaration of the Fourth International at the Antifascist Forum in Brazil (2026).

## Project structure

- `index.html` — Complete single-file site (HTML + CSS + JS, no build step)

## Design

- Dark theme with light mode via `prefers-color-scheme`
- Strong red and black palette; CSS custom properties for all theme colors
- Playfair Display (headings) + Inter (body) + Noto Sans Arabic (RTL)
- Scroll-triggered fade-in animations, animated diagonal stripe texture, red scroll progress bar
- Fourth International logo as hero background graphic and closing mark

## Multilingual

Four languages: English (default), French, Spanish, Arabic. Translations live in a JS `translations` object keyed by `data-i18n` attributes. Arabic triggers RTL layout via `dir="rtl"` on `<html>`.

When editing text, update both the HTML element and the corresponding key in the `translations` object for all four languages.

## Print

The print button calls `window.print()`. A `@media print` block strips dark backgrounds, animations, and navigation, producing a clean black-on-white layout suitable for PDF export. To suppress browser-generated headers/footers (URL, date), uncheck "Headers and footers" in the browser print dialog.

## Key conventions

- No build tools, bundlers, or dependencies — everything is in the single HTML file
- All theme colors use CSS custom properties defined in `:root` and overridden in the `prefers-color-scheme: light` media query
- Section dividers use the `.star-ornament` class (star SVG flanked by gradient lines)
- The English text matches the formatting of the canonical docx source (paragraph breaks, bold, italics)
