# Kern CCD Project Management Dashboard — brand notes

Source-of-truth for visual identity is the **Kern CCD / CREL Style Guide**.

## Palette

| Role | Hex | Use |
|------|-----|-----|
| KCCD Red | `#bc1823` | Primary brand accent — active nav, KPI highlight, primary CTA. Used sparingly. |
| KCCD Red (deep) | `#8b0f1a` | Hover state for the primary accent. |
| KCCD Orange | `#ff914d` | Secondary accent / data callouts. Pair with red, never replace. |
| KCCD Dark Grey | `#545454` | Secondary text, neutral fills. |
| KCCD Light Grey | `#d9d9d9` | Dividers, soft surfaces. |
| Black | `#000000` | Body text on light surfaces. |
| White | `#ffffff` | Default surface. |

All other surfaces in the dashboard (`#fbfbfd` page bg, `#f5f5f7` muted bg, `#e5e5ea` hairline border, `#1d1d1f` ink) are derived to play well with the official palette and stay Apple-minimalist.

## Typography

| Role | Stack |
|------|-------|
| Display | `Cambria`, `Source Serif 4`, `Georgia`, `Times New Roman`, serif |
| Body | `Calibri`, `Inter`, `Arial`, `Helvetica Neue`, sans-serif |

Cambria and Calibri come from the CREL style guide. The web fallbacks (Source Serif 4 + Inter, served via Google Fonts) keep the dashboard readable for visitors who don't have Microsoft fonts installed.

## Voice for dashboard copy

- **District-facing, not funder-facing.** Write like the dashboard is shown to the people doing the work, not the people writing the check. *"A simple view of how spending lines up with the plan,"* not *"Quarterly burn-rate variance analysis."*
- **Calm and concrete.** Avoid hype. Avoid "powered by AI." State the fact and move on.
- **Short paragraphs.** Every section's lead paragraph should fit on one screen line on mobile.

## Visual language

- Lots of white space. Generous padding on cards.
- Hairline 1px borders for separation, not heavy shadows.
- Color is reserved for moments — KCCD red on the active sidebar item, on a single KPI bar, on the "Year 2" timeline accent. Never paint a full surface red.
- Charts use neutral greys + a single red dataset to differentiate Year 2 from Year 1.

## Logo

If a KCCD wordmark is required, drop it as `assets/kccd-wordmark.png` and reference from the sidebar. The current sidebar uses a stylized monogram (red rounded square + chart icon) as a neutral placeholder so the dashboard renders cleanly without the official logo.

## Don't

- Don't use neon variants of the red.
- Don't pair red and orange in the same chart series.
- Don't drop in a stock-photo background.
- Don't use shadows heavier than `0 4px 16px rgba(0,0,0,0.06)`.
