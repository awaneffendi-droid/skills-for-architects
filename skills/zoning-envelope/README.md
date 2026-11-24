# /as:zoning-envelope

Interactive 3D zoning envelope viewer as a Claude Code skill. Generates a single HTML file (Three.js loaded from a CDN) that renders the buildable envelope for any lot — exact lot polygon from GIS data, setback zones, extruded volumes, height caps, and interactive orbit controls.

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](../../LICENSE)

## Install

```bash
# Via plugin system
claude plugin marketplace add AlpacaLabsLLC/skills-for-architects
claude plugin install as@skills-for-architects
```

## Usage

First, run a zoning analysis to generate a report:

```
/as:zoning-analysis-id Jl. Contoh No. 1, Kelurahan X, Kecamatan Y, Kota Z
```

Then generate the 3D viewer:

```
/as:zoning-envelope path/to/analisis-tata-ruang-jl-contoh-1.md
```

Or search by keyword:

```
/as:zoning-envelope jl-contoh
```

Or auto-detect the most recent report:

```
/as:zoning-envelope
```

## What it renders

- **Exact lot polygon** from a surveyed plot boundary or CAD file (metres) — not a simplified rectangle
- **Setback zones** as colored ground overlays with dashed inset boundaries
- **Buildable volumes** — base, tower, galibo — extruded from the lot polygon at correct heights
- **Height cap** — amber plane at maximum building height
- **Edge-length labels** on lot boundary edges
- **Height labels** with dashed reference lines
- **Parameters panel** — KDB, KLB, KDH, max floor area, height limits, GSB
- **Interactive controls** — orbit, zoom, pan (Three.js OrbitControls)

## How it works

The skill reads the `## Envelope Data` JSON block from a zoning analysis report. This block contains:

The following invented geometry illustrates the interface only; it is not a zoning rule or site analysis.

```json
{
  "lot_poly": [[0, 0], [30, 0], [30, 22], [0, 22]],
  "unit": "m",
  "setbacks": { "front": 4, "rear": 2, "lateral1": 1.5, "lateral2": 1.5 },
  "volumes": [
    { "type": "base", "inset": 2, "h_bottom": 0, "h_top": 12, "label": "synthetic volume" }
  ],
  "height_cap": 12,
  "info": { "title": "Synthetic geometry fixture", "zone": "unverified" },
  "stats": {}
}
```

The skill then:

1. Parses the polygon and envelope parameters
2. Computes inset polygons for setback zones and building volumes
3. Triangulates the polygons (ear-clipping) for 3D extrusion
4. Generates a single HTML file that loads Three.js from a CDN (internet required to view)
5. Opens it in the browser

## Key features

- **Self-correcting polygon inset** — automatically detects and corrects for different polygon winding directions across data sources
- **Multi-volume envelopes** — podium + tower
- **Multi-scenario support** — toggle buttons for comparing development scenarios (for example per-plot versus amalgamated plots)
- **Works with any polygon source** — surveyed coordinates (SRGI2013/WGS 84, UTM) or manual coordinates

## Dependency

This skill requires a zoning analysis report as input. It does not perform zoning calculations — run `/as:zoning-analysis-id` first.

## Demo

[Live demo (250 Hudson Street)](https://alpa.llc/demos/zoning-envelope.html)

## License

MIT
