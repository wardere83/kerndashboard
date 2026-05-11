# Kern CCD Project Management Dashboard

A single-file, no-build dashboard for Kern Community College District's **VR EEO Faculty Development & Peer Mentoring Program** (2026–2028 EEO IBP Tier 1 grant, $150,000).

Live preview: [`wardere83.github.io/kerndashboard`](https://wardere83.github.io/kerndashboard) (auto-deploys from `main` via GitHub Pages).

---

## What's in here

```
.
├── index.html            ← the entire dashboard (HTML/CSS/JS, ~1,000 lines)
├── brand/
│   ├── BRANDING.md       ← KCCD / CREL palette, typography, voice guidelines
│   └── palette.css       ← reusable CSS custom properties for downstream use
├── assets/               ← drop the official KCCD wordmark + favicon here
├── docs/
│   ├── getting-started.md
│   ├── branding.md
│   └── data-model.md
├── .github/workflows/pages.yml  ← GitHub Pages deploy on every push to main
└── LICENSE                ← MIT
```

No build step. `index.html` includes Chart.js from a CDN and Google Fonts as a Cambria/Calibri fallback. Open the file directly in a browser, or serve the repo statically.

## Sections

1. **Overview** — project meta, participating colleges, total/Y1/Y2/Indirect KPIs, cross-college highlight.
2. **Goals & Objectives** — four program goals.
3. **Workplan & Timeline** — Year 1 / Year 2 / Combined view, five phases from infrastructure through closeout.
4. **Outcomes & Metrics** — five measurable outcomes with Year-2 targets.
5. **Budget Breakdown** — Y1 vs Y2 line-by-line + Chart.js bar chart by object code + a full expenditure table that locks to exactly $150,000.
6. **Spend-Down Monitor** — per-year On Track / Off Track toggle, persisted to `localStorage` (key: `kernPmdState.v1`). Off-track years roll up into the Project Pacing alert card.

## Brand

The dashboard uses the official Kern CCD / CREL palette (Red `#bc1823`, Light Grey `#d9d9d9`, Dark Grey `#545454`, Black, Orange `#ff914d`) and Cambria / Calibri typography (with Source Serif 4 / Inter as web fallbacks). Visual language: Apple-minimalist neutral. Red shows up only as a quiet accent — never as a full-surface fill. See [`brand/BRANDING.md`](brand/BRANDING.md) for the full guide.

## Deploy

Pushes to `main` trigger [`.github/workflows/pages.yml`](.github/workflows/pages.yml), which publishes the repo root to GitHub Pages. Enable Pages in repo Settings → Pages → Source: **GitHub Actions** the first time. The live site lands at `https://wardere83.github.io/kerndashboard` (or your custom domain if you drop a `CNAME` file in the repo root).

## Run locally

```
git clone https://github.com/wardere83/kerndashboard.git
cd kerndashboard
python3 -m http.server 8080
# open http://localhost:8080
```

That's all the tooling there is. No npm, no bundler, no framework.

## Editing program data

The data lives at the top of the `<script>` block in `index.html`:

- `PROJECT` — high-level project metadata + yearly budget split.
- `EXPENDITURES` — line-by-line spend used to render both the expenditure table and the Chart.js chart. Total must sum to `PROJECT.funding`; the table will show whatever you put here, but the budget bar widths assume the existing distribution.

Update those two structures and the rest of the dashboard recalculates on next page load.

## Audience

The dashboard is **district-facing** — Bobby Becka, Rachel Tatro-Duarte, Cathi Jacob, and the program leads at BC, Cerro Coso, and Porterville. Tone, copy, and language are tuned for them, not for CCCCO program officers. See the **Voice** section of [`brand/BRANDING.md`](brand/BRANDING.md).

## License

MIT for documentation, configuration, brand-token files. See [`LICENSE`](LICENSE).
