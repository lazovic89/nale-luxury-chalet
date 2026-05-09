# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static marketing website for **Nale Luxury Chalet** — a luxury rental property in Bosnia and Herzegovina. No build tools, no package manager, no backend.

Live site: https://naleluxchalet.com/

## Development

No build step required. Open any `index.html` in a browser to preview. No dev server, no npm, no linting, no tests.

To deploy: copy the entire directory to any web server or CDN (GitHub Pages, Netlify, Vercel, S3, etc.).

## Architecture

### Multilingual Structure

Four language versions, each a standalone HTML file:

| File | Language |
|---|---|
| `index.html` | Serbian (root, canonical) |
| `en/index.html` | English |
| `de/index.html` | German |
| `fr/index.html` | French |

Language subdirectory files use relative paths (`../assets/`, `../logo/`) to reach shared resources. SEO is handled via `hreflang` tags in each file's `<head>`.

The Serbian root version (`index.html`) is the most fully formatted source; the other language files are more compact/minified.

### Page Structure

All versions share an identical 8-section layout:
`navbar → hero → amenities strip → about → gallery → banner → location → contact → footer`

Navigation uses anchor links (`#section-id`) with smooth scrolling — no client-side router.

### Tech Stack

- **HTML5** — semantic markup
- **Tailwind CSS via CDN** — utility classes plus custom theme extensions
- **Vanilla JavaScript** — all interactivity inline in `<script>` tags at bottom of `<body>`
- **Google Fonts CDN** — Cormorant Garamond (headings), Inter (body)

### Brand / Design System

Defined as Tailwind theme extensions inside a `<script type="text/javascript">` block in each file's `<head>`:

- `charcoal`: `#1a1a1a` — dark background
- `cream`: `#f5f0e8` — light text/background
- `gold`: `#c9a96e` — accent color

### JavaScript Features

All JS is inline, no external scripts:

- **Navbar scroll effect** — adds blur/background on scroll
- **Lightbox gallery** — click image to expand; supports keyboard arrows, touch swipe, ESC to close
- **Mobile hamburger menu** — toggle show/hide
- **Smooth scroll** — anchor click handler

### Assets

- `assets/` — 21 WebP images (property photos)
- `logo/` — favicons, PWA icons, `site.webmanifest`
- `logo.jpg` — main logo image

### External Integrations

Contact and booking handled entirely through third-party links (no forms processed server-side):
- Airbnb, Booking.com (booking platforms)
- WhatsApp, Viber (messaging)
- Instagram (social)
- Google Maps embedded iframe (location section)
