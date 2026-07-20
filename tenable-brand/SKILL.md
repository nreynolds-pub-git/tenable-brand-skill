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

## Dark mode vs. Light mode

Both modes are valid Tenable brand expressions. Dark mode (Soft Black backgrounds,
White text, Yellow accents) is the iconic look — that's what most Tenable marketing
and product UI uses. Light mode (White backgrounds, Soft Black text, Yellow as
accent fills only) is appropriate for content-heavy contexts: documentation,
reports, dense forms, anywhere users may print, or accessibility scenarios where
dark mode increases eye strain.

The palette is identical across both modes — only the role of each color flips.

### Dark mode tokens

| Role | Value | Notes |
|------|-------|-------|
| Background | `#1E2426` | Soft Black |
| Surface (cards, panels) | `rgba(255,255,255,0.05)` | overlay on Soft Black |
| Elevated surface (hover) | `rgba(255,255,255,0.08)` | |
| Subtle border | `rgba(255,255,255,0.10)` | |
| Prominent border | `rgba(255,255,255,0.20)` | |
| Primary text | `#FFFFFF` | |
| Secondary text | `rgba(255,255,255,0.60)` | |
| Muted text | `rgba(255,255,255,0.40)` | |
| Accent (as text) | `#E7FF00` | ✓ allowed |
| Accent (as fill) | `#E7FF00` with `#1E2426` text inside | primary buttons, CTAs |

### Light mode tokens

| Role | Value | Notes |
|------|-------|-------|
| Background | `#FFFFFF` | White |
| Surface (cards, panels) | `rgba(30,36,38,0.04)` | overlay on White |
| Elevated surface (hover) | `rgba(30,36,38,0.06)` | |
| Subtle border | `rgba(30,36,38,0.10)` | |
| Prominent border | `rgba(30,36,38,0.20)` | |
| Primary text | `#1E2426` | Soft Black |
| Secondary text | `rgba(30,36,38,0.70)` | |
| Muted text | `rgba(30,36,38,0.50)` | |
| Accent (as text) | ✗ NEVER `#E7FF00` on white | fails contrast |
| Accent (as fill) | `#E7FF00` with `#1E2426` text inside | only sanctioned use |

### The Highlight Yellow asymmetry

This is the rule that genuinely differs between modes:

- **Dark mode**: Yellow works as text OR as fill. Both `#E7FF00` on `#1E2426`
  and `#1E2426` on `#E7FF00` pass contrast.
- **Light mode**: Yellow is **fill-only**. Yellow text on white is forbidden.
  A "primary action" in light mode is always a yellow rectangle with Soft Black
  text inside — never yellow text floating on a white background.

This is the most common brand violation in light mode. If you're tempted to put
yellow text on white, either change the text color to Soft Black or wrap the
text in a yellow fill.

### Severity colors work in both modes

The data palette (Orange, Yellow, Blue, Green, Gray) is bright enough to read
in both modes without adjustment. Always pair the severity color (as background)
with Soft Black text — white text on the severity colors fails contrast:

```html
<!-- Critical badge — works in dark OR light mode -->
<span style="background: #FF8837; color: #1E2426; padding: 2px 8px; border-radius: 3px;">
  CRITICAL
</span>
```

### Implementation patterns

**Option A — respect OS preference automatically** (no UI toggle, simplest):

```css
:root {
  --bg: #FFFFFF;
  --bg-surface: rgba(30, 36, 38, 0.04);
  --border: rgba(30, 36, 38, 0.10);
  --text: #1E2426;
  --text-muted: rgba(30, 36, 38, 0.60);
  --accent: #E7FF00;
}

@media (prefers-color-scheme: dark) {
  :root {
    --bg: #1E2426;
    --bg-surface: rgba(255, 255, 255, 0.05);
    --border: rgba(255, 255, 255, 0.10);
    --text: #FFFFFF;
    --text-muted: rgba(255, 255, 255, 0.60);
    --accent: #E7FF00;
  }
}

body {
  background: var(--bg);
  color: var(--text);
}
```

**Option B — explicit toggle** (gives users a choice; recommended for long-session tools):

```css
:root,
[data-theme="light"] {
  --bg: #FFFFFF;
  --bg-surface: rgba(30, 36, 38, 0.04);
  --border: rgba(30, 36, 38, 0.10);
  --text: #1E2426;
  --text-muted: rgba(30, 36, 38, 0.60);
  --accent: #E7FF00;
}

[data-theme="dark"] {
  --bg: #1E2426;
  --bg-surface: rgba(255, 255, 255, 0.05);
  --border: rgba(255, 255, 255, 0.10);
  --text: #FFFFFF;
  --text-muted: rgba(255, 255, 255, 0.60);
  --accent: #E7FF00;
}
```

```js
// Toggle handler
const toggle = () => {
  const current = document.documentElement.getAttribute('data-theme') || 'light';
  document.documentElement.setAttribute('data-theme', current === 'dark' ? 'light' : 'dark');
};
```

**Tailwind dark mode**: add `darkMode: 'class'` to `tailwind.config.js`, then use `dark:` variants:

```html
<div class="bg-white dark:bg-tenable-black text-tenable-black dark:text-white">
  <button class="bg-tenable-yellow text-tenable-black px-4 py-2 rounded">
    Primary action  <!-- yellow fill works in both modes -->
  </button>
</div>
```

```js
document.documentElement.classList.toggle('dark');
```

### Mode choice heuristic

- **Default to dark mode** for: dashboards, demos, hero pages, marketing surfaces,
  any UI showcasing the brand
- **Use light mode** for: long-form reading (docs, reports), data-entry forms,
  printable content, accessibility-first scenarios
- **Support both with a toggle** for: customer-facing tools used in long sessions

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

> **Font-lock rule.** Tenable output is set in **Work Sans** (Google Fonts).
> That's the only font — for web, HTML artifacts, Google Slides, PowerPoint /
> .pptx, Word / .docx, matplotlib, charts, dashboards, reports, everything.
> If you are about to emit type in any other family — **Calibri**, Arial,
> Helvetica, Roboto, "system-ui" on its own, the pptx default, the docx default,
> or a Word/PowerPoint theme font — stop and switch to Work Sans. There is no
> case in which a Tenable deliverable ships with Calibri. If the tool you're
> using defaults to something else, the fix is to override the font on every
> run, not to leave it.

Set letter-spacing to **-3%** (`tracking: -0.03em` in Tailwind, `letter-spacing:
-0.03em` in CSS) on Work Sans everywhere. This is a real, sanctioned brand
adjustment.

Fall back chain (CSS):
```css
font-family: "Work Sans", system-ui, -apple-system, sans-serif;
letter-spacing: -0.03em;
```

### Weights

Tenable uses five weights. Do not introduce Black, ExtraBold, or Bold — they are
not part of the system. Use the exact face name in code (not the family name
plus a `bold`/`weight` flag; see the PowerPoint note).

| Weight             | CSS `font-weight` |
|--------------------|-------------------|
| Work Sans Thin     | 100               |
| Work Sans Light    | 300               |
| Work Sans          | 400 (Regular)     |
| Work Sans Medium   | 500               |
| Work Sans SemiBold | 600               |

### Hierarchy

Every piece of typography Tenable produces slots into one of these five levels.
**All levels are sentence case.** Do not use Title Case, ALL CAPS (except for
short tags/eyebrows), or ad-hoc weights outside this table.

| Level        | Weight            | Case          | Used for                                                              |
|--------------|-------------------|---------------|-----------------------------------------------------------------------|
| XL Headline  | **Light**         | sentence case | Covers, divider slides, section openers, billboards, oversized comps  |
| Headline     | Regular           | sentence case | Standard headlines on content slides / pages                          |
| Subhead      | Regular           | sentence case | Supports the headline with detail; long-form content                  |
| Body copy    | Light             | sentence case | All primary reading text                                              |
| Caption      | Medium            | sentence case | Captions, headers, footers, small notes; +5% letter-spacing           |

Scale follows the **50/50 rule**: each level is no more than half the size of the
level above it (e.g. 72 pt XL → 36 pt Headline → 18 pt Subhead → 9 pt Body).
Line-spacing: 90% for headlines, 110% for subheads, 125% for body/caption.
Letter-spacing: 0% for everything, +5% for caption only; and the -3% Work Sans
adjustment applies on top of that when Work Sans is the actual face.

### Slide titles (all decks, all tools)

Slide titles — cover titles, section headers, per-slide headlines on 16:9 decks —
are **Work Sans Light** by default. They are XL Headlines in the hierarchy above.
The only exception is a small in-content sub-title that acts as a Headline rather
than a cover — that one is Work Sans Regular. When in doubt on a slide, use Light.

Do **not** produce a bold slide title. Do not use `run.font.bold = True` to
"darken" a title — that forces the Bold face and defeats Light. Change the size
or color for emphasis instead.

### PowerPoint / .pptx — python-pptx enforcement

**This is the section most likely to be skipped, and it's the one that produced
the Calibri bug.** python-pptx does **not** apply the deck's theme font unless
you explicitly set `run.font.name` on every run you create — and the default
PowerPoint theme font is Calibri. Setting the text on a title placeholder
(`slide.shapes.title.text = "..."`) inherits the theme font, which will be
Calibri unless overridden per-run.

**Rule:** every run in every shape in every slide gets its font name set
explicitly. No exceptions — not for titles, not for body, not for table cells,
not for chart labels, not for footers.

Drop-in helper — paste this into any script that produces or edits a Tenable
deck, and route every run through it:

```python
from pptx.util import Pt
from pptx.dml.color import RGBColor

TENABLE_BLACK  = RGBColor(0x1E, 0x24, 0x26)
TENABLE_WHITE  = RGBColor(0xFF, 0xFF, 0xFF)
TENABLE_YELLOW = RGBColor(0xE7, 0xFF, 0x00)

# Work Sans face-name mapping. Use the specific face name (e.g. "Work Sans
# Light"), NOT the family name plus a bold flag — the bold flag forces the
# Bold face and defeats Light / Medium.
_FACES = {
    "xl_headline": "Work Sans Light",     # cover / section / big titles
    "headline":    "Work Sans",           # standard headline
    "subhead":     "Work Sans",           # subhead
    "body":        "Work Sans Light",     # body copy
    "caption":     "Work Sans Medium",    # captions, headers, footers
}

def apply_tenable_font(run, level="body", size_pt=None, color=None):
    """Force a run onto the Tenable typography system.

    `level` is one of: xl_headline, headline, subhead, body, caption.
    Always call this on runs you create — python-pptx will otherwise fall back
    to the theme font (Calibri) and produce an off-brand deck.
    """
    run.font.name = _FACES[level]
    run.font.bold = False           # explicit — do not let a template override
    run.font.italic = False
    if size_pt is not None:
        run.font.size = Pt(size_pt)
    if color is not None:
        run.font.color.rgb = color
```

Creating a new title on a slide — the pattern is *never* `.text = "..."`,
always add a run and style it:

```python
title_tf = slide.shapes.title.text_frame
title_tf.clear()                       # drop the inherited theme run
p = title_tf.paragraphs[0]
run = p.add_run()
run.text = "Optimizing business outcomes"
apply_tenable_font(run, level="xl_headline", size_pt=54, color=TENABLE_WHITE)
```

**Updating an existing legacy deck** (the common case — a customer's old-brand
deck that needs to be re-skinned). Setting the theme won't fix the runs that
already have hard-coded `<a:latin typeface="Calibri"/>` markup. You have to walk
every run and reset the font:

```python
from pptx import Presentation

prs = Presentation("legacy.pptx")

def walk_runs(shape):
    if shape.has_text_frame:
        for para in shape.text_frame.paragraphs:
            for run in para.runs:
                yield run
    if shape.has_table:
        for row in shape.table.rows:
            for cell in row.cells:
                for para in cell.text_frame.paragraphs:
                    for run in para.runs:
                        yield run
    if shape.shape_type == 6:      # GROUP
        for child in shape.shapes:
            yield from walk_runs(child)

for slide in prs.slides:
    for shape in slide.shapes:
        for run in walk_runs(shape):
            # Decide the level from the placeholder / size / position.
            # When in doubt, treat placeholder idx 0 (title) as xl_headline
            # and everything else as body.
            level = "xl_headline" if (
                shape.has_text_frame and shape.is_placeholder
                and shape.placeholder_format.idx == 0
            ) else "body"
            apply_tenable_font(run, level=level)

prs.save("legacy_rebranded.pptx")
```

Before saving any `.pptx`, do a final self-check: unzip the file and grep for
`Calibri` in `ppt/slides/*.xml`. If any hits come back, a run was missed —
loop over them again. Getting zero Calibri hits is the definition of "done."

### Word / .docx — python-docx enforcement

Same principle as PowerPoint: python-docx will use the document's default
theme (Calibri on a blank doc) unless you set `run.font.name` explicitly. For
Word body reports, the mapping collapses to two faces most of the time —
Work Sans Light for body copy, Work Sans Medium for headings / captions:

```python
from docx.shared import Pt, RGBColor

TENABLE_BLACK = RGBColor(0x1E, 0x24, 0x26)

def apply_tenable_font_docx(run, level="body", size_pt=None):
    faces = {"heading": "Work Sans", "subheading": "Work Sans",
             "body": "Work Sans Light", "caption": "Work Sans Medium",
             "xl_headline": "Work Sans Light"}
    run.font.name = faces[level]
    run.font.bold = False
    if size_pt is not None:
        run.font.size = Pt(size_pt)
    run.font.color.rgb = TENABLE_BLACK
```

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

### CSS variables (with light + dark modes)

```css
:root,
[data-theme="light"] {
  /* Primary palette */
  --tenable-black: #1E2426;
  --tenable-white: #FFFFFF;
  --tenable-yellow: #E7FF00;

  /* Light-mode role tokens */
  --bg: #FFFFFF;
  --bg-surface: rgba(30, 36, 38, 0.04);
  --border: rgba(30, 36, 38, 0.10);
  --text: #1E2426;
  --text-muted: rgba(30, 36, 38, 0.60);
  --accent: #E7FF00;

  /* Data palette (mode-agnostic) */
  --data-gray: #44494B;
  --data-blue: #4EA5FF;
  --data-green: #71FFC6;
  --data-purple: #BB8FF2;
  --data-orange: #FF8837;

  /* Severity (mode-agnostic; always paired with --tenable-black text) */
  --sev-critical: #FF8837;
  --sev-high: #E7FF00;
  --sev-medium: #4EA5FF;
  --sev-low: #71FFC6;
  --sev-info: #44494B;
}

[data-theme="dark"] {
  --bg: #1E2426;
  --bg-surface: rgba(255, 255, 255, 0.05);
  --border: rgba(255, 255, 255, 0.10);
  --text: #FFFFFF;
  --text-muted: rgba(255, 255, 255, 0.60);
  --accent: #E7FF00;
}

@media (prefers-color-scheme: dark) {
  :root:not([data-theme]) {
    --bg: #1E2426;
    --bg-surface: rgba(255, 255, 255, 0.05);
    --border: rgba(255, 255, 255, 0.10);
    --text: #FFFFFF;
    --text-muted: rgba(255, 255, 255, 0.60);
  }
}

body {
  background: var(--bg);
  color: var(--text);
  font-family: "Work Sans", system-ui, -apple-system, sans-serif;
  letter-spacing: -0.03em;
}
```

### Tailwind config block

```js
// tailwind.config.js
export default {
  darkMode: 'class',  // toggle dark mode by adding `dark` class to <html>
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
      },
      letterSpacing: {
        'tenable': '-0.03em',   // apply on every text element
      },
    },
  },
};
```

Use `dark:` variants on every component that needs both modes:

```html
<body class="bg-white dark:bg-tenable-black text-tenable-black dark:text-white">
  <div class="bg-black/[0.04] dark:bg-white/5 border border-black/10 dark:border-white/10 rounded-lg p-4">
    <h2 class="text-tenable-black dark:text-white">Card title</h2>
    <p class="text-tenable-black/60 dark:text-white/60">Secondary text</p>
    <button class="bg-tenable-yellow text-tenable-black px-4 py-2 rounded">
      Primary action
    </button>
  </div>
</body>
```

In HTML, load Work Sans:

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

- [ ] Mode is chosen intentionally (dark for dashboards/demos, light for docs/forms)
- [ ] Background is Soft Black (dark mode) or White (light mode)
- [ ] Body text contrasts against background — never yellow on white, never white on yellow
- [ ] In **light mode**, Highlight Yellow appears only as a fill (with Soft Black text inside), never as text
- [ ] Highlight Yellow is reserved for ≤ 1–2 actionable items per view
- [ ] Font is **Work Sans** with -3% tracking — **never Calibri**, Arial, Helvetica, Roboto, or a template default
- [ ] For .pptx / .docx output, every run has `run.font.name` set explicitly (theme fonts are not enough)
- [ ] Slide titles are **Work Sans Light** (the face name, not the bold flag); body is Work Sans Light; captions are Work Sans Medium
- [ ] Text is sentence case at every hierarchy level
- [ ] Severity badges use Orange/Yellow/Blue/Green/Gray fills with Soft Black text — not Red, not white text
- [ ] If reproducing the Iris, only doing so in official Tenable deliverables

If all pass, the output is on brand. For .pptx specifically, the last-mile check
is: unzip the file and grep `ppt/slides/*.xml` for `Calibri` — zero hits = done.
