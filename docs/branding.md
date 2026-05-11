# Branding deep-dive

Authoritative source: **Kern CCD / CREL Style Guide.** See also [`../brand/BRANDING.md`](../brand/BRANDING.md) for the at-a-glance summary.

## Where the palette is applied

Every color in `index.html` is defined once at the top of the `<style>` block via CSS custom properties, then referenced everywhere downstream. To rebrand a section, change the variable, not a hex value buried in a class definition.

```css
:root {
  --kccd-red:        #bc1823;
  --kccd-red-deep:   #8b0f1a;
  --kccd-red-soft:   #f5d4d7;
  --kccd-orange:     #ff914d;
  --kccd-grey-dark:  #545454;
  --kccd-grey-light: #d9d9d9;
  --kccd-black:      #000000;

  --bg:           #fbfbfd;
  --bg-surface:   #ffffff;
  --bg-surface-2: #f5f5f7;
  --border:       #e5e5ea;

  --text-primary:   #1d1d1f;
  --text-secondary: #424245;
  --text-muted:     #6e6e73;
}
```

The same tokens are extracted to `brand/palette.css` for use in any downstream project that needs to inherit the KCCD palette without copying the entire `index.html`.

## Where red shows up (and where it doesn't)

The dashboard treats `--kccd-red` as a moment, not a surface:

- ✅ Sidebar active-item left border and text
- ✅ One KPI card's accent bar (the lead "Total Budget" or "Total Award" tile)
- ✅ A thin top stripe on the Year 2 column to differentiate Y2 visually
- ✅ Inline anchor dot on each college pill
- ✅ Indirect-line bar in the budget breakdown (calling out the 5% line)
- ✅ Mobile bottom-nav active state
- ✅ One Chart.js dataset (Year 2)
- ❌ Page backgrounds — never
- ❌ Card surfaces — never
- ❌ Whole-section gradients — never

## Typography

| Role | Stack |
|------|-------|
| Display (`h1`, `h2`, `h3`, KPI numerals, card titles) | `Cambria, 'Source Serif 4', Georgia, 'Times New Roman', serif` |
| Body (everything else) | `Calibri, Inter, Arial, 'Helvetica Neue', sans-serif` |

Cambria and Calibri are the CREL-mandated faces and are installed on virtually all Microsoft Office machines and most Macs. Source Serif 4 and Inter are loaded from Google Fonts as web fallbacks so the dashboard reads correctly on Chromebooks, Linux laptops, and any browser that lacks the system fonts.

## Voice

The Kern CCD dashboard is *district-facing*, not *funder-facing*. Internal staff are the audience. The voice rules:

- **Calm.** Not breathless. Not "AI-powered." Not "revolutionary."
- **Concrete.** *"Mark a year Off Track to surface it in the alerts panel,"* not *"Configure variance reporting heuristics."*
- **Short.** Lead paragraph of every section fits on one screen line on a phone.
- **Honest about state.** If a year is off track, the dashboard says so plainly. If nothing's flagged, the alert panel says *"Everything looks good."*

## When to use orange

The CREL palette includes `--kccd-orange #ff914d`. Today the dashboard reserves orange for *future* use (callouts, status accents, secondary chart series). The Year-2 differentiator and the active state are both red. If/when a third color tier is needed, pair red and orange — never replace red with orange.

## When to drop in the official wordmark

The sidebar currently uses a stylized red rounded-square + chart icon as a neutral placeholder. To replace with the real wordmark:

1. Add `assets/kccd-wordmark-light.png` (black wordmark, transparent background).
2. In `index.html`, replace the `.sidebar-logo .logo-mark` block with an `<img>` tag pointing at the new asset.
3. Bump the version and update [`CHANGELOG.md`](../CHANGELOG.md).
