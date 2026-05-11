# Changelog

## [Unreleased]

### Added
- Initial Kern CCD Project Management Dashboard (`index.html`):
  - Six sections (Overview, Goals & Objectives, Workplan & Timeline, Outcomes & Metrics, Budget Breakdown, Spend-Down Monitor) wired to a sidebar nav + mobile bottom nav.
  - KPI cards for Total Budget / Y1 / Y2 / Indirect.
  - Year 1 / Year 2 / Combined workplan tabs.
  - Five-metric outcomes table.
  - Y1 vs Y2 budget breakdown with bar visualization and per-line spend.
  - Chart.js bar chart of expenditure by object code.
  - Full expenditure detail table totaling exactly $150,000.
  - Interactive Spend-Down Monitor with per-year On/Off Track toggles, persisted in localStorage.
- Apple-minimalist visual treatment using the official Kern CCD / CREL palette and Cambria / Calibri typography (with Source Serif 4 / Inter web fallbacks).
- Brand guide (`brand/BRANDING.md`) and reusable palette token sheet (`brand/palette.css`).
- Docs (`docs/`): getting-started, branding deep-dive, data model.
- MIT license for documentation and assets.
- GitHub Pages workflow (`.github/workflows/pages.yml`) — every push to `main` deploys `index.html` to GitHub Pages.
