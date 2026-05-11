# Data model

The dashboard is data-driven from two JavaScript constants near the bottom of `index.html`. Update those, refresh, done.

## `PROJECT`

```js
const PROJECT = {
  id: 'kern',
  title: 'Kern CCD — VR EEO Faculty Development and Peer Mentoring Program',
  funding: 150000,
  yearlyBudget: { y1: 122638, y2: 27362 },
};
```

| Field | Type | What it drives |
|-------|------|----------------|
| `funding` | number | Total grant award. Displayed in the Total Budget KPI. The sum of `EXPENDITURES[].amount` must match this. |
| `yearlyBudget.y1` | number | Year 1 budget. Displayed in Year 1 KPI and used by the Spend-Down Monitor row. |
| `yearlyBudget.y2` | number | Year 2 budget. Same. |

## `EXPENDITURES`

An array of line items. Each entry:

```js
{ year: 'Year 1' | 'Year 2', code: '1000' | '3000' | '4000' | '5000' | '7000', label: 'Human description', amount: 12345 }
```

| Object code | Meaning |
|-------------|---------|
| `1000` | Certificated salaries |
| `3000` | Employee benefits |
| `4000` | Supplies and equipment |
| `5000` | Services and operating expenses |
| `7000` | Indirect (institutional overhead — 5% of direct in this program) |

Source: CCCCO standard object codes for community college grants.

The dashboard sums per-year and per-code on render to populate:

- The "All Expenditures" table on the Budget section
- The Chart.js bar chart of expenditure by object code (Year 1 vs Year 2)

The per-budget-card line breakdown on the Budget section is currently hardcoded for clarity. If you change `EXPENDITURES`, also update the matching `<div class="budget-line">` entries on the Y1/Y2 budget cards so the per-line amounts stay in sync.

## Spend-Down state

Per-year On / Off Track status is stored in the browser's `localStorage` under key `kernPmdState.v1`:

```json
{ "Year 1": "off", "Year 2": "on" }
```

Allowed values: `"on"` (or absent → defaults to on) and `"off"`. Click the status badge in the Year-by-Year View table to flip it. The Project Pacing alert card rolls up any years marked off into a visible alert.

State is per-browser, per-user — there is no server-side sync. If a stakeholder needs to see your view, share a screenshot.

## Adding a participating college

Open `index.html`, find `<div class="college-row">` inside the Participating Colleges card, and add another `<span class="college-pill">`. That's the only change required. The KPIs are not parameterized by college count.

## Adding a goal

Goals live in the Goals & Objectives section as `<li class="stack-item">` entries. Each goal has a numbered tile (the `.stack-num`), a one-line title, and a body paragraph. Pattern follows what's already there.

## Adding a metric

Outcomes & Metrics is a plain HTML table. Append a `<tr>` with `#`, metric name, and Year-2 target columns. No JS changes needed.

## Adding a phase

Workplan phases live inside `.timeline-year-card` blocks under the Year 1 and Year 2 tab panes, and as `.stack-item` entries under the Combined View pane. To add a phase: add it in all three places so the three tabs stay in sync.
