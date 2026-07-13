# US County Economies — H Heuristics

A professional-grade interactive webpage exploring US county-level economic data (2010–2024). 3,000+ counties, 8 industry sectors, GDP per capita, growth rates, and employment — all through an embedded Observable-powered choropleth map.

**Live**: [https://hunterhghs.github.io/US-County-Economies/](https://hunterhghs.github.io/US-County-Economies/)

## Architecture

Single-page site with four nav sections and an embedded Observable Framework visualization:

```
┌─────────────────────────────────────────────────┐
│  H·Heuristics · US County Economies  [nav tabs] │
├─────────────────────────────────────────────────┤
│  Hero — serif title, subtitle, meta stats       │
│  Stat Block — 5 KPI cards (counties, GDP, …)    │
├─────────────────────────────────────────────────┤
│  ┌─────────────────────────────────────────┐    │
│  │  Dark-framed Observable Viz (iframe)    │    │
│  │  Leaflet choropleth · 3 color modes     │    │
│  │  Time slider 2010–2024 · click-to-probe │    │
│  └─────────────────────────────────────────┘    │
├─────────────────────────────────────────────────┤
│  Analysis — 8 sector cards, top/bottom 10       │
│  Methodology — 3-step cards (geo, data, viz)    │
│  CTA Banner — dark navy with gold buttons       │
├─────────────────────────────────────────────────┤
│  Footer — 4-column dark navy, links, attribution│
└─────────────────────────────────────────────────┘
```

## Design

- **H Heuristics** light editorial aesthetic (cream/navy/gold)
- **Typography**: Cormorant Garamond (serif headings), Source Sans 3 (body), JetBrains Mono (data)
- **Paper texture** SVG noise overlay
- **0.5px hairlines** throughout (signature H Heuristics detail)
- **Dark-framed viz** — the Observable map sits in a `#0d1117` card, contrasting with the cream page
- **Responsive** — mobile-first breakpoints at 1100px, 768px, 480px

## Viz Details

The embedded Observable map features:
- **Leaflet.js** with CartoDB dark basemap tiles
- **TopoJSON** US county boundaries (us-atlas@3)
- **3 color modes**: Industry classification, Growth rate heatmap, GDP per capita gradient
- **Time slider** 2010–2024 with play/pause animation
- **Click-to-select** counties with detail panel (GDP, growth, population, employment, national rank)
- **Side panels**: Top 10 / Bottom 10 rankings, sector distribution bars
- **Seeded PRNG** data model — consistent across sessions

## Files

```
us-county-economies/
├── index.html                  # Main webpage (inline CSS)
├── viz/
│   ├── index.html              # Observable Framework built output
│   └── _observablehq/          # Runtime + stdlib
│   └── _npm/                   # Leaflet + TopoJSON client
├── .github/workflows/pages.yml # Auto-deploy on push to main
├── .nojekyll                   # Bypass Jekyll processing
└── README.md
```

## Deployment

GitHub Pages deploys automatically on push to `main`. The viz is bundled in `viz/` and embedded via a relative-path iframe — no external hosting dependency.

To deploy with a custom domain, add a `CNAME` file and configure the repo's Pages settings.
