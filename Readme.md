# Jerome Walker — Fitness Ecosystem 

A premium, monochrome fitness platform combining tracking-brand identity, a coach
discovery directory, a live product catalog, a gear customizer, and a snacks
mini-mall — built on top of the Task 1 landing page.

## Project Overview

Jerome Walker started as a responsive landing page  and has been
extended here into a small multi-page, dynamic web application for Task. It
keeps the same premium/minimal/masculine visual identity (black, off-white,
charcoal, single lime accent, Manrope + Inter typography) across every page.

The site is **plain HTML5, CSS3, and vanilla JavaScript** — no build step,
no framework, no `npm install`. Each page is one single, self-contained
`.html` file with its CSS and JavaScript inline (organised into clearly
commented sections), so there's nothing to hunt across multiple files for.
The only external folder is `images/`, since that's where you'll drop in
your own product photos.

```
jerome-walker-simple/
├── index.html        # homepage (CSS + JS inline)
├── coaches.html       # coach discovery (CSS + JS inline)
├── equipment.html      # shop + signature gear (CSS + JS inline)
├── customize.html       # gear customizer (CSS + JS inline)
├── mall.html              # mini mall (CSS + JS inline)
├── images/
│   ├── logo.jpg, hero.png
│   └── products/
│       ├── gear/        # Signature Gear photos (equipment.html)
│       ├── customize/   # flask / bottle / pouch / backpack photos
│       └── mall/         # snack photos
├── README.md
└── TASK3_REPORT.md
```

## Pages

| Page | Purpose |
|---|---|
| `index.html` | Homepage — hero, feature grid, dashboard mock, testimonials, explore links |
| `coaches.html` | Coach discovery grid with local coach data |
| `equipment.html` | **Task 3 core**: live product catalog (Fake Store API) + a local "Signature Gear" section |
| `customize.html` | Product customizer — Flask / Water Bottle / Snacks Pouch / Backpack, with color, size and message options |
| `mall.html` | Mini mall — snacks (energy bars, granola bars, energy drinks, Pocari Sweat), local static data |

## Features

- Responsive header with mobile hamburger nav, shared across every page
- Product catalog dynamically fetched from a live external API
- Search, category filtering, and price sorting on both shop pages
- Product detail modal with focus handling and `Escape`-to-close
- Loading, error, and empty states for the API-driven catalog and the mall
- Local "Signature Gear" and mini-mall sections built for easy photo swaps —
  every product has an `image` path you can point at your own photography
- Gear customizer with live-updating preview (photo, color frame, size,
  engraved/patch message) across four product types
- Toast notifications for cart actions
- Scroll-reveal animations that respect `prefers-reduced-motion`

## Technologies Used

- HTML5 (semantic elements: `header`, `nav`, `main`, `section`, `article`, `footer`)
- CSS3 — custom properties, Flexbox, Grid, media queries
- Vanilla JavaScript (ES6+) — `fetch`, DOM APIs, `IntersectionObserver`
- [Fake Store API](https://fakestoreapi.com/products) — external, live data source

## API Used & Integration Explanation

`equipment.html`'s main catalog calls `https://fakestoreapi.com/products` with
`fetch()` on page load. The response is stored in memory, categories are
derived from the returned data (and relabelled into fitness-store-appropriate
names, since the API's own categories are generic), and the product grid is
re-rendered whenever the person searches, filters, or sorts. A `try/catch`
around the fetch (and a `.ok` check on the response) covers the error state;
an empty filtered result covers the empty state; a skeleton grid covers the
loading state.

The "Signature Gear" section above it and the entire `mall.html` catalog use
**local static data on purpose** — they're the spots meant for your own
product photography rather than the API's stock images, so they don't call
the network at all (aside from a short simulated delay in `mall.html` so the
loading state stays honest rather than decorative).

## Component Structure

There's no framework-level component system (see the technology note above),
but the HTML/CSS/JS is organised the same way component-based systems are —
by repeatable, class-scoped UI pieces reused across pages:

- Header / mobile nav (identical markup + script per page)
- Product card (`.shop-card`) — used by both the API catalog and the mall
- Product modal (`.shop-modal-backdrop`) — used by both shop pages
- Coach card (`.coach-card`)
- Customizer tab + preview frame (`.customize-tab`, `.customize-preview-frame`)
- Toast (`.toast`) — shared feedback component across every page

## Setup Instructions / How to Run Locally

No build tools required.

1. Download or clone the project folder.
2. Open `index.html` directly in a browser, **or** serve the folder locally
   for a closer-to-production setup:
   ```bash
   # from inside the project folder
   python3 -m http.server 5500
   # then visit http://localhost:5500
   ```
3. Navigate the site using the header nav (Home, Coaches, Gear, Customize, Mall).

## Live Deployment

Live URL: 
GitHub repo: 


