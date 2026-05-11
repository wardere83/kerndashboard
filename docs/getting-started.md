# Getting started

The Kern CCD Project Management Dashboard is a single-file HTML application. There's no framework, no build step, and no server.

## View it live

If GitHub Pages is enabled on this repo, the dashboard publishes to:

```
https://wardere83.github.io/kerndashboard
```

The `.github/workflows/pages.yml` workflow pushes to GitHub Pages on every commit to `main`.

## Run it locally

```bash
git clone https://github.com/wardere83/kerndashboard.git
cd kerndashboard
python3 -m http.server 8080
```

Open http://localhost:8080 in any modern browser. Chart.js and Google Fonts are pulled from CDNs; you need an internet connection on first load (after that, both are cached by the browser).

## Open it directly

Because the dashboard is a single file with no module imports, you can also just open `index.html` in a browser. Chart.js may or may not work from a `file://` URL depending on the browser's CDN security policy; serving via a local HTTP server is the reliable path.

## Section overview

| Section | What's on it |
|---------|--------------|
| **Overview** | Project meta, participating colleges, top-line KPIs |
| **Goals & Objectives** | Four program goals + supporting detail |
| **Workplan & Timeline** | Year 1 / Year 2 / Combined views of the five-phase roadmap |
| **Outcomes & Metrics** | Five measurable outcomes with Year-2 targets |
| **Budget Breakdown** | Y1 vs Y2 budget by object code + full expenditure table |
| **Spend-Down Monitor** | Per-year On / Off Track toggle with alert aggregation |

## Updating data

Open `index.html` and find the `<script>` block near the bottom. The data you'll touch most:

- `PROJECT.yearlyBudget` — the Year 1 / Year 2 budget split.
- `EXPENDITURES` — every line item. Total **must** sum to `PROJECT.funding` (currently $150,000), otherwise the dashboard will display a mismatch.

Everything else (KPI cards, budget bars, expenditure table, Chart.js chart) reads from those two structures and re-renders on next page load.

## Sharing with stakeholders

The dashboard is designed for direct sharing — no login, no backend. Send the GitHub Pages URL or this repo link. The Spend-Down Monitor state is per-browser (localStorage), so each viewer can mark their own track-status without affecting anyone else.

## Adjusting branding

See [`docs/branding.md`](branding.md) and the brand guide at [`../brand/BRANDING.md`](../brand/BRANDING.md). The palette lives at the top of `index.html` inside `:root { ... }` and is mirrored to `brand/palette.css` for downstream reuse.
