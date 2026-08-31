# Harmattan — an educational micro-site, built with HTML & CSS only

A small multi-page site about the Harmattan: the dry, dusty seasonal wind
that shapes life across West Africa every year. Built to demonstrate
**semantic HTML structure and advanced CSS engineering — with zero
JavaScript anywhere in the project.**

**[Live site →](#)** *https://koidioble.github.io/harmattan/*

## Why this project exists

It started as a small pricing-page demo. It grew into two things at once:

1. A real, factually-researched explainer on an actual natural phenomenon
   — proper headers, paragraphs, lists, tables, figures, and cross-page
   navigation, the way a real content site is built.
2. A showcase of what pure CSS can still do without a framework or a
   single line of JavaScript: theme switching, language switching, modals,
   toggles, and animation.

Rather than pick one, the project keeps both — as separate pages that are
honest about what they are.

## Site map

| Page | Purpose |
|---|---|
| `index.html` | Home — overview and quick-facts table |
| `formation.html` | How the wind forms — step timeline, an SVG pressure-system diagram, and a synthesized ambient audio clip |
| `impact.html` | What it affects — health, aviation, agriculture, energy — as cards and a comparison table |
| `regions.html` | Who it reaches — a country/region table and a CSS-only bar chart of typical season length |
| `pricing.html` | The original CSS-only interactivity playground (fictional pricing page, sign-in modal, language switcher, live theme swap) |

All five pages share one `style.css` and are connected by a real, working
top navigation and footer — standard `<a href="...">` links between
distinct files, not just in-page anchors.

## What's demonstrated where

**Structure (semantic HTML)**
- Proper heading hierarchy (`h1`–`h4`), `<nav>`, `<main>`, `<footer>`, `<figure>`/`<figcaption>`
- Real `<table>` elements with `<caption>`, `<thead>`, `scope="row"`/`scope="col"` — not divs pretending to be tables
- Ordered and unordered lists used where they're semantically correct (the formation timeline is an `<ol>`, sources are a `<ul>`)

**Layout (CSS)**
- CSS Grid for the pricing cards, impact cards, and page-navigation cards
- Flexbox for the timeline, nav, and bar chart rows
- A full custom-property (CSS variable) design system, including a
  second full palette swapped in for light mode

**Media & navigation**
- An inline SVG diagram of the two pressure systems (self-drawn, so no
  copyright concerns), styled with the same CSS variables as the rest of
  the site
- A short ambient wind sound in `assets/wind-ambience.wav` — this is
  **synthesized from filtered noise in Python**, not a recording, purely
  so it could be embedded here without any licensing question, while
  still demonstrating the `<audio>` element with real, working controls
- Real hyperlinked navigation between five distinct HTML files

**Language switching (EN / FR / ES) — site-wide**
- Every page — Home, Formation, Impact, Regions, and the UI Patterns
  playground — is fully translated into French and Spanish
- Built the same way as the theme toggle: radio inputs + CSS `:has()`
  show and hide the matching `[lang]` span, no JavaScript
- The switcher sits in the header next to the theme toggle on every page,
  so it's always in the same place

**Responsiveness**
- Every page adapts through three breakpoints down to mobile, using
  `@media` queries — grids collapse to single columns, nav simplifies,
  spacing tightens

**Animation without JavaScript**
- Hover states and lift transitions on every card and button
- A slow, ambient background gradient drift (`formation.html`, `index.html`, etc.)
- An animated bar-chart fill on `regions.html` using a CSS keyframe transform
- A subtle fade-up entrance on page sections
- All animation respects `prefers-reduced-motion`

## Known, deliberate limitations

Because there is genuinely no JavaScript anywhere in this project:

- **Theme and language choice don't persist across pages.** Each page's
  toggle and switcher are independent — navigating to a new page resets
  both back to dark mode / English. A real production version would use
  `localStorage` (via a few lines of JS) or a server-rendered cookie to
  remember the choice.
- **The page `<title>` and the `lang="en"` attribute on `<html>` don't
  change** even when French or Spanish is selected, since CSS can't
  touch either of those.
- **The SVG diagram labels on `formation.html` stay in English** in all
  three languages — translating text inside inline SVG via CSS is
  possible but fragile across browsers, so it was left out rather than
  shipped half-working. The figure caption explains this.
- **The "Further reading" source links are left in English** on
  `impact.html` and `regions.html`, since they link to real external
  articles that are themselves in English — translating the link text
  would misrepresent what's on the other end.

These are called out here on purpose. Knowing exactly where a
JavaScript-free approach runs out of road — and being upfront about it
— is part of what this project is meant to show.

## Tech

- HTML5 (semantic elements, tables, figures, native `<audio>`)
- CSS3 (Grid, Flexbox, custom properties, `:has()`, `:target`, keyframe animation, media queries)
- Google Fonts (Fraunces, Inter, Space Grotesk)
- Python (one-time offline script, not part of the site itself) to synthesize the ambient audio clip
- No JavaScript, no dependencies, no build step

## Run it locally

```bash
git clone https://github.com/koidioble/harmattan.git
cd harmattan
open index.html   # or double-click the file
```

No install step — it's static files.

## Deploy

**GitHub Pages**
1. Push this repo to GitHub
2. Settings → Pages → Deploy from branch → `main` / root
3. Your live URL appears in a minute or two

**Netlify**
1. Drag the project folder onto [app.netlify.com/drop](https://app.netlify.com/drop)
2. Done — instant live URL

## Sources

Facts about the Harmattan referenced across the content pages are drawn
from and cross-checked against:

- [Harmattan — Wikipedia](https://en.wikipedia.org/wiki/Harmattan)
- [Harmattan — SKYbrary Aviation Safety](https://skybrary.aero/articles/harmattan)
- [West Africa's hazardous winds — The Conversation](https://theconversation.com/west-africas-hazardous-winds-harmattan-carries-more-than-dust-it-also-spreads-disease-252426)
- [West Africa's Hazardous Winds — JSTOR Daily](https://daily.jstor.org/west-africas-hazardous-winds/)
- [The African Meningitis Belt — University of Oxford](https://maidenlab.zoo.ox.ac.uk/african-meningitis-belt)

---

Built by [Koidio Y. Blé](https://koidioble.com) —  Software Engineer | Flutter, Firebase, Mobile, Web & Cloud Applications
