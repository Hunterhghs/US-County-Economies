# US County Economies — Project Overview

## Goal
Build a professional-grade H Heuristics webpage about US County Economies (2010–2024) that integrates an advanced ObservableHQ data visualization as its centerpiece.

## Architecture
A single-page website with the Observable visualization embedded via iframe:

```
┌─────────────────────────────────────────────┐
│  H HEURISTICS  ·  US County Economies      │
├─────────────────────────────────────────────┤
│  Overview Section                           │
│  - What this dashboard shows                │
│  - Key metrics: 3,000+ counties, 8 sectors  │
│  - Data methodology                         │
├─────────────────────────────────────────────┤
│  ┌─────────────────────────────────────┐    │
│  │                                     │    │
│  │   OBSERVABLE HQ VISUALIZATION       │    │
│  │   (iframe embed)                    │    │
│  │   - Interactive county choropleth   │    │
│  │   - Color by industry/growth/gdp    │    │
│  │   - Time slider 2010-2024           │    │
│  │   - Click counties for details      │    │
│  │                                     │    │
│  └─────────────────────────────────────┘    │
├─────────────────────────────────────────────┤
│  Informational Section                      │
│  - County rankings                          │
│  - Sector breakdown                         │
│  - Key findings                             │
├─────────────────────────────────────────────┤
│  Footer: H Heuristics · Observable Pro      │
└─────────────────────────────────────────────┘
```

## Technical Plan

### 1. ObservableHQ Visualization
The existing US County Economic Map from Observable Framework test project at:
`/Users/hunterhughes/.reasonix/global-workspace/us-county-dashboard/src/index.md`

This contains:
- Leaflet choropleth of 3,000+ US counties
- 3 color modes (Industry, Growth, GDP/capita)
- Time slider 2010-2024
- Click-to-select county with detail panel
- Dark theme (#0d1117 background, #161b22 cards, #58a6ff accent)

The viz should be deployed as a standalone Observable Framework site (build with `npm run build`, deploy to GitHub Pages) so it can be iframe-embedded.

### 2. Webpage (built with Veles/Fable 5)
A standalone HTML file with:
- **Dark professional theme** matching H Heuristics brand (#0d1117 bg, #161b22 cards)
- **Header**: H Heuristics logo/branding, nav links
- **Hero section**: Title, subtitle, key stats (3,000+ counties, 8 sectors, 2010-2024)
- **Visualization section**: iframe embed of the ObservableHQ viz, full-width
- **Info section**: Cards with county highlights, sector descriptions, methodology notes
- **Footer**: H Heuristics copyright, links

### 3. Design Specs
- **Background**: #0d1117 (dark)
- **Cards**: #161b22 with #30363d borders
- **Text**: #c9d1d9 primary, #8b949e muted
- **Accent**: #58a6ff (blue), #3fb950 (green), #d2991d (gold), #f85149 (red)
- **Font**: -apple-system, BlinkMacSystemFont, system-ui sans-serif
- **Typography**: Clean, professional, generous whitespace
- **Responsive**: Mobile-friendly with stacked layout

## Files to Create
```
us-county-economies/
├── index.html              # Main webpage
├── styles.css              # (or inline in index.html)
├── .github/workflows/
│   └── pages.yml           # GitHub Pages deploy
├── CNAME                   # us-county-economies.hheuristics.com
└── README.md
```

## Key Data Points for Content
- 3,143 US counties tracked
- 8 industry sectors: Technology, Manufacturing, Finance, Healthcare, Energy, Agriculture, Tourism, Government
- 2010-2024 time range with yearly data
- GDP per capita ranging from ~$300 to ~$100,000
- Growth rates from 0.5% to 4.5% annually
- Observable Pro-powered visualization (no attribution banner)

## Deployment
- GitHub Repo: https://github.com/Hunterhghs/US-County-Economies
- GitHub Pages with custom domain
- Observable viz hosted separately on ObservableHQ or as static Framework site

## Observable Viz Reference
The working visualization lives in the Observable Framework test project.
Key patterns that work reliably:
- Single `import * as L from "npm:leaflet"` import
- `import("npm:topojson-client")` for TopoJSON
- US county GeoJSON from `https://cdn.jsdelivr.net/npm/us-atlas@3/counties-10m.json`
- Inline data generation (no Python data loaders needed)
- Dark CartoDB tiles: `cartocdn.com/dark_all/{z}/{x}/{y}{r}.png`
- Manual event handlers (no OrbitControls needed for 2D maps)
