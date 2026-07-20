---
name: tenable-brand
description: >
  Canonical Tenable brand guidelines — exact color hex codes, typography rules,
  accessibility constraints, and ready-to-use code snippets for producing on-brand
  Tenable output. Use this skill whenever building anything that should look like
  it belongs to Tenable: dashboards, reports, web UIs, Claude React/HTML artifacts,
  presentations, PDFs, POV success criteria documents, security data visualizations,
  email templates, or internal tools shown to customers. Also use this whenever the
  user mentions "Tenable branding," "brand colors," "make this look like Tenable,"
  or shows any sign of preparing customer-facing material for a Tenable audience.
  Trigger even when the user only describes the visual outcome (e.g. "make a dashboard
  for our pipeline data") and is a Tenable employee — assume Tenable styling unless
  they say otherwise.
---

# Tenable Brand

Canonical reference for producing on-brand Tenable output. All values here come
directly from the Tenable Brand Guidelines and are safe to use without further
verification.

## Tagline

> Control over chaos

Use sparingly — it's a positioning line, not a header. Appropriate as a subtitle on
covers, in headers of polished deliverables, or as a tagline next to the wordmark.

---

## Primary palette

Three colors. That's it. Anything beyond these three is from the data palette below
and is reserved for charts and categorical UI.

| Name             | Hex       | Use                                                 |
|------------------|-----------|-----------------------------------------------------|
| Soft Black       | `#1E2426` | Default background for dark-mode UI, body text on light bg, primary text on yellow |
| White            | `#FFFFFF` | Default background for light-mode UI, body text on dark bg |
| Highlight Yellow | `#E7FF00` | Accent only — see "Highlight Yellow rules" below     |

## Accessibility — required color combinations

These six are the only sanctioned combinations. The ✗ pairs fail contrast and must
never be used:

| Combination                         | Allowed? |
|-------------------------------------|----------|
| White text on Soft Black            | ✓        |
| Soft Black text on White            | ✓        |
| Soft Black text on Highlight Yellow | ✓        |
| Highlight Yellow text on Soft Black | ✓        |
| Highlight Yellow text on White      | ✗ never  |
| White text on Highlight Yellow      | ✗ never  |

If you find yourself wanting yellow text on a white background, change either the
background to Soft Black or the text to Soft Black. Same for white text on yellow.

## Highlight Yellow rules

Highlight Yellow has a specific role and is the easiest color in the palette to
misuse. Follow these in order of importance:

1. **Reserve for actionable items and key information.** Buttons, links, focus
   states, the one important number on a dashboard, the CTA. Not decoration.
2. **Don't saturate large areas.** Don't make covers, full backgrounds, or hero
   panels yellow. Use it as an accent against Soft Black or White.
3. **Don't highlight too much.** If half the items on a page are highlighted,
   nothing is highlighted.
4. **Never use it for body text on white.** It fails contrast. See accessibility
   table above.

When in doubt, default to Soft Black + White and use yellow for the single most
important element on the screen.

---

## Data palette

Use these *only* for data visualization where you need more than three colors to
encode categorical information (chart segments, severity levels, source types).
Don't pull from this palette for UI chrome.

| Name             | Hex       |
|------------------|-----------|
| Highlight Yellow | `#E7FF00` |
| White            | `#FFFFFF` |
| Gray             | `#44494B` |
| Blue             | `#4EA5FF` |
| Green            | `#71FFC6` |
| Purple           | `#BB8FF2` |
| Orange           | `#FF8837` |

### Severity color mapping for security data

This is the canonical mapping for Tenable security data visualizations (vulnerability
severity, finding severity, risk levels). It's been tuned against the data palette
to keep yellow's "key information" meaning intact:

| Severity | Color            | Hex       |
|----------|------------------|-----------|
| Critical | Orange           | `#FF8837` |
| High     | Highlight Yellow | `#E7FF00` |
| Medium   | Blue             | `#4EA5FF` |
| Low      | Green            | `#71FFC6` |
| Info     | Gray             | `#44494B` |

Don't introduce red — it's not in the palette. Critical uses Orange instead, which
reads as urgent without breaking brand.

---

## Typography

| Context                                    | Font                            |
|--------------------------------------------|---------------------------------|
| Print, native apps, anywhere Aeonik is licensed | **Aeonik Pro**             |
| Web, Google Slides, anywhere Aeonik isn't available | **Work Sans** (Google Fonts) |

When using Work Sans as a substitute, **set letter-spacing to -3%** (`tracking: -0.03em`
in Tailwind, `letter-spacing: -0.03em` in CSS). This is a real, sanctioned brand
adjustment that closes the visual gap to Aeonik.

Fall back chain (CSS):
```css
font-family: "Work Sans", system-ui, -apple-system, sans-serif;
```

### Slide titles

**Titles on slides are always Work Sans Light.** This applies to every deck —
cover titles, section headers, and per-slide headlines. Do not use Work Sans
Regular, Medium, SemiBold, or Bold for slide titles, and do not rely on the
`bold` flag to darken a title; that forces the Bold face regardless of the
typeface name and defeats the Light weight.

Set the typeface explicitly:

- **Python-pptx:** `run.font.name = 'Work Sans Light'` and leave `run.font.bold`
  unset (or `False`).
- **OpenXML (raw):** `<a:latin typeface="Work Sans Light"/>` with no `b="1"`
  attribute on the `<a:rPr>`.
- **HTML / CSS:** `font-family: "Work Sans Light", "Work Sans", system-ui,
  sans-serif; font-weight: 300;`
- **Google Slides:** pick "Work Sans Light" from the font dropdown; don't set
  the bold toggle.

Slide subheads, table headers, and label chrome should use **Work Sans Medium**
(also set as a distinct typeface name, not via the bold flag). Body copy stays
on Work Sans Regular.

Preview note: LibreOffice does not ship Work Sans Light and will substitute a
heavier weight in QA renders. Trust the typeface name in the XML, not the
preview, when Work Sans Light is specified — it will render Light in PowerPoint
on any machine with the Work Sans family installed.

### Line length

Brand spec for legibility:
- Headlines: 4–15 characters per line
- Body copy: 40–70 characters per line

If body lines hit 100+ characters in your design, break into columns or reduce
the container width.

---

## The Iris

The Iris is Tenable's logomark — two overlapping heptagons. It represents "control
over chaos through perspective" and is shorthand for the Tenable brand.

**Important:** don't reproduce the Iris in independent/community projects that
aren't official Tenable products. Use a generic geometric placeholder instead and
let the customer/user know it's a placeholder. The Iris belongs in official Tenable
deliverables (decks, marketing, product UI) where you have explicit authority to
use brand assets.

If you do need to place the Iris in an official deliverable, use the assets from
the official Tenable brand portal — don't recreate it from scratch (vertex angles
matter).

---

## Ready-to-use snippets

### CSS variables

```css
:root {
  /* Primary */
  --tenable-black: #1E2426;
  --tenable-white: #FFFFFF;
  --tenable-yellow: #E7FF00;

  /* Data palette */
  --data-gray: #44494B;
  --data-blue: #4EA5FF;
  --data-green: #71FFC6;
  --data-purple: #BB8FF2;
  --data-orange: #FF8837;

  /* Severity mapping */
  --sev-critical: #FF8837;
  --sev-high: #E7FF00;
  --sev-medium: #4EA5FF;
  --sev-low: #71FFC6;
  --sev-info: #44494B;
}

body {
  background: var(--tenable-black);
  color: var(--tenable-white);
  font-family: "Work Sans", system-ui, -apple-system, sans-serif;
  letter-spacing: -0.03em;
}

/* Slide title convention — always Light */
.slide-title {
  font-family: "Work Sans Light", "Work Sans", system-ui, sans-serif;
  font-weight: 300;
}
```

### Tailwind config block

```js
// tailwind.config.js
export default {
  theme: {
    extend: {
      colors: {
        'tenable-black': '#1E2426',
        'tenable-yellow': '#E7FF00',
        'data-gray': '#44494B',
        'data-blue': '#4EA5FF',
        'data-green': '#71FFC6',
        'data-purple': '#BB8FF2',
        'data-orange': '#FF8837',
        'sev-critical': '#FF8837',
        'sev-high': '#E7FF00',
        'sev-medium': '#4EA5FF',
        'sev-low': '#71FFC6',
        'sev-info': '#44494B',
      },
      fontFamily: {
        sans: ['"Work Sans"', 'system-ui', '-apple-system', 'sans-serif'],
        'slide-title': ['"Work Sans Light"', '"Work Sans"', 'system-ui', 'sans-serif'],
      },
      letterSpacing: {
        'aeonik-match': '-0.03em',
      },
    },
  },
};
```

In HTML, load Work Sans (weight 300 is Light):

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Work+Sans:wght@300;400;500;600;700&display=swap" rel="stylesheet">
```

### Python — for matplotlib / Plotly chart styling

```python
TENABLE = {
    "black": "#1E2426",
    "white": "#FFFFFF",
    "yellow": "#E7FF00",
}

DATA_PALETTE = {
    "gray":   "#44494B",
    "blue":   "#4EA5FF",
    "green":  "#71FFC6",
    "purple": "#BB8FF2",
    "orange": "#FF8837",
    "yellow": "#E7FF00",
}

SEVERITY_COLORS = {
    "Critical": "#FF8837",
    "High":     "#E7FF00",
    "Medium":   "#4EA5FF",
    "Low":      "#71FFC6",
    "Info":     "#44494B",
}
```

### Python-pptx — slide title convention

```python
# ALWAYS use this pattern for slide titles.
run = para.add_run()
run.text = "Slide Title Here"
run.font.name = "Work Sans Light"   # not "Work Sans" + bold
run.font.size = Pt(38)
# do NOT set run.font.bold — that forces the Bold face and defeats Light
```

### Python-docx — set text color in a Word report

```python
from docx.shared import RGBColor

# Soft Black for body text
run.font.color.rgb = RGBColor(0x1E, 0x24, 0x26)

# Highlight Yellow for emphasis (use sparingly!)
run.font.color.rgb = RGBColor(0xE7, 0xFF, 0x00)
```

---

## Quick reference card

When producing any Tenable-branded output, run through this checklist:

- [ ] Background is Soft Black or White (not yellow)
- [ ] Body text contrasts against background (not yellow-on-white or white-on-yellow)
- [ ] Highlight Yellow is reserved for ≤ 1–2 actionable items per view
- [ ] Font is Aeonik Pro (or Work Sans with -3% tracking)
- [ ] **Slide titles are Work Sans Light (typeface name, not bold flag)**
- [ ] Severity uses Orange/Yellow/Blue/Green/Gray — not Red
- [ ] If reproducing the Iris, only doing so in official Tenable deliverables

If all seven pass, the output is on brand.
