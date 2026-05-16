# Visual Reference — Nexus Benefit Solutions / Amaze Pages

Source: extracted from the production bundle at `nexusbenefitsolutions.com/amaze`
(stylesheet `/assets/index-oIEzZUh8.css`, app bundle `/assets/index-CMc2EPpm.js`).

The site is a Vite + React SPA styled with Tailwind on top of a shadcn/ui token
layer (HSL-based design tokens with light and dark themes). Routes confirmed in
the bundle: `/amaze`, `/amaze-health`, `/amaze-health#individual`,
`/amaze-health#wellbeing`, `/amaze-individual`.

---

## Color Palette

The token system is HSL-based with paired light and dark themes. Hex values
below are the rendered equivalents.

### Brand / primary
| Role | Token (HSL) | Hex | Notes |
|------|-------------|-----|-------|
| Primary (CTA, links, ring) | `17 63% 48%` light / `17 63% 44%` dark | `#C75A2C` / `#B8522A` | Terracotta / burnt sienna. The signature accent — used for buttons, focus rings, sidebar primary. |
| Primary foreground | `0 0% 100%` | `#FFFFFF` | Text on primary buttons. |

### Neutrals (light theme — the default surface look)
| Role | Token (HSL) | Hex |
|------|-------------|-----|
| Background | `60 11% 98%` | `#FAFAF7` (warm parchment off-white) |
| Foreground (body text) | `150 33% 18%` | `#1F3D2E` (deep forest green — used as the primary text color, not black) |
| Card | `86 13% 91%` | `#E8EADF` |
| Card border | `86 13% 85%` | `#D6DAC9` |
| Secondary / Accent surface | `86 13% 88%` | `#DDE0D3` (soft sage-tinted neutral) |
| Muted | `86 10% 90%` | `#E5E6DD` |
| Muted foreground | `140 10% 40%` | `#5C7066` |
| Border | `86 13% 87%` | `#D9DDCC` |
| Ring (focus) | `17 63% 48%` | `#C75A2C` |
| Destructive | `0 65% 45%` | `#BD2828` |

### Dark theme (used in dark sections / hero overlays)
| Role | Hex |
|------|-----|
| Background | `#0E1F17` (near-black forest) |
| Foreground | `#F2F2EC` (warm bone) |
| Card | `#1A2E22` |
| Sidebar accent | `#243A2E` |

### Observed accent / supporting hex values
Pulled directly from the compiled CSS, ranked by frequency. These are used in
illustrations, icon backgrounds, and section accents:

- `#1F3D2E` — primary text / dark forest (brand neutral)
- `#B8522A` — terracotta primary (alt shade)
- `#022C22`, `#064E3B`, `#065F46`, `#047857`, `#059669`, `#10B981`, `#34D399`,
  `#6EE7B7`, `#A7F3D0`, `#D1FAE5`, `#ECFDF5` — emerald scale (used for
  health/wellness affirming iconography and chips)
- `#06B6D4`, `#0891B2`, `#22D3EE`, `#67E8F9` — cyan scale (used sparingly,
  often paired with emerald for medical/clinical accents)
- `#FBBF24` — amber (rare, callouts)
- `#0F172A`, `#111827`, `#374151`, `#4B5563`, `#9CA3AF`, `#D1D5DB`, `#E5E7EB`
  — slate scale for chrome / dividers

> **Takeaway:** the brand pairs a warm off-white background with deep forest
> green type and a terracotta accent. Emerald greens are the supporting
> palette for "health/wellness" visuals; cyan appears for clinical content.
> Pure black is never used.

---

## Typography

Loaded from Google Fonts in the document head:

```
https://fonts.googleapis.com/css2?family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,400;0,9..40,500;0,9..40,600;0,9..40,700;1,9..40,400&family=DM+Serif+Display:ital@0;1&display=swap
```

### Stacks
```css
--font-sans:  "DM Sans", -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
--font-serif: "DM Serif Display", Georgia, serif;
--font-mono:  Menlo, monospace;
```

### Usage pattern
- **DM Serif Display** — display headlines, hero H1, large pull quotes.
  Regular (400) and italic. Optical-size aware.
- **DM Sans** — everything else: subheads, body, UI, buttons. Weights in use:
  300 / 400 / 500 / 600 / 700. Italic 400.
- **Georgia / Times** appears in `!important` overrides — used in the
  prose/article blocks (Tailwind Typography plugin defaults).

### Sizes / rhythm (representative — common values found in the bundle)
- Base body: `1rem` (16px), line-height ~1.6
- Body small / chip: `0.875rem` (14px)
- Lead paragraph: `1.125rem`–`1.25rem`
- Section eyebrow / tag: `0.75rem`, uppercase, tracked
- H3 / card title: `1.25rem`–`1.5rem`
- H2 / section title: `1.875rem`–`2.5rem` (serif)
- H1 / hero: `3rem`–`4.5rem` responsive (serif, weight 400, tight tracking)
- Border radius default: `0.5rem` (`--radius: .5rem`)

### Heading character
Headings rely on DM Serif Display's natural high-contrast strokes. They are
**not bold** — they read as editorial / publication-style rather than corporate
sans bold. Sentence case or Title Case (not all caps) for H1/H2. Eyebrows
above sections are the only all-caps elements and are letter-spaced.

---

## Spacing & Layout

- Tailwind default spacing scale (`0.25rem` increments).
- Section vertical padding most commonly `py-16` to `py-24` on desktop
  (`4rem`–`6rem`), `py-12` on mobile.
- Content max width: ~`max-w-7xl` (1280px) for full sections, `max-w-3xl`
  (~768px) for prose blocks.
- Generous whitespace — sections rarely feel dense. Cards have `p-6` to `p-8`
  internal padding.
- Grid patterns: 2-up and 3-up card grids with `gap-6` / `gap-8`.

---

## Component Patterns

### Buttons (primary CTA)
- Background: terracotta `#C75A2C` (`hsl(var(--primary))`)
- Text: white
- Radius: `0.5rem`
- Padding: ~`px-5 py-3` (medium) / `px-6 py-3.5` (large)
- Weight: DM Sans 500
- A subtle "gleam sweep" animation on hover (`@keyframes ctaGleamSweep` —
  a translucent diagonal shine moves across the button).
- A "press-response" micro-interaction scales the button slightly on `:active`,
  respecting `prefers-reduced-motion`.

### Secondary buttons
- Transparent / outlined on the sage neutral, or filled sage `#DDE0D3` with
  dark forest text `#1F3D2E`.

### Cards
- Background: `#E8EADF` (card token) or white in some sections
- Border: `1px solid #D6DAC9`
- Radius: `0.5rem`
- Shadow: very light or none. The site favors borders and tonal separation
  over drop shadows.

### Navigation
- A custom underline-draw effect on nav links (`.nav-underline-draw:before`
  with a transition). Underlines animate in from the left on hover.
- Sticky header that hides for `@media print`.

### Section eyebrows
- Small uppercase label (`0.75rem`, letter-spaced) in muted forest, sitting
  above a serif H2. Classic editorial pattern.

### Imagery
- Hero uses a full-bleed photographic poster (`/amaze-hero-poster.jpg`)
  layered with a dark forest gradient overlay for legibility of white serif
  type on top.
- Iconography leans on emerald/teal tinted strokes — not flat brand-colored
  icons. Suggests Lucide-style line icons with custom color treatment.

### Motion
- Reduced-motion safeguards on every animation (`prefers-reduced-motion`).
- `premium-reveal` class — sections fade/slide in on scroll.
- All transitions feel slow and confident, not snappy/SaaS-y.

---

## Tone Summary (2-3 sentences)

The Amaze pages read **editorial, warm, and confidently calm** — closer to a
boutique wellness brand or a New England consultancy than to a typical
insurance site. The pairing of deep forest green type on warm parchment with
terracotta accents, set in DM Serif Display, gives it a grounded, human,
slightly aspirational feel. It's minimal but not sterile: lots of whitespace,
no drop shadows, generous serif headlines, and one disciplined accent color
doing all the CTA work.

---

## Ready-to-Use CSS Variables (drop into Cornerstone hub stylesheet)

```css
/* === Cornerstone Well-Being — Nexus Amaze visual language === */
@import url('https://fonts.googleapis.com/css2?family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,400;0,9..40,500;0,9..40,600;0,9..40,700;1,9..40,400&family=DM+Serif+Display:ital@0;1&display=swap');

:root {
  /* Type */
  --font-sans:  "DM Sans", -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  --font-serif: "DM Serif Display", Georgia, "Times New Roman", serif;
  --font-mono:  Menlo, ui-monospace, monospace;

  /* Brand palette (hex for clarity; HSL also provided below) */
  --color-bg:            #FAFAF7;  /* warm parchment */
  --color-surface:       #E8EADF;  /* card */
  --color-surface-alt:   #DDE0D3;  /* secondary / sage */
  --color-muted:         #E5E6DD;
  --color-border:        #D9DDCC;
  --color-fg:            #1F3D2E;  /* deep forest — primary text */
  --color-fg-muted:      #5C7066;
  --color-primary:       #C75A2C;  /* terracotta */
  --color-primary-hover: #B8522A;
  --color-primary-fg:    #FFFFFF;
  --color-accent-green:  #10B981;  /* emerald — wellness chips/icons */
  --color-accent-teal:   #0891B2;  /* clinical accent */
  --color-destructive:   #BD2828;

  /* Dark surfaces (for hero overlays / dark sections) */
  --color-dark-bg:       #0E1F17;
  --color-dark-fg:       #F2F2EC;
  --color-dark-surface:  #1A2E22;

  /* Geometry */
  --radius: 0.5rem;
  --radius-lg: 0.75rem;
  --radius-pill: 9999px;

  /* Spacing scale (Tailwind-style) */
  --space-1: 0.25rem;
  --space-2: 0.5rem;
  --space-3: 0.75rem;
  --space-4: 1rem;
  --space-6: 1.5rem;
  --space-8: 2rem;
  --space-12: 3rem;
  --space-16: 4rem;
  --space-24: 6rem;

  /* Section rhythm */
  --section-py: clamp(3rem, 6vw, 6rem);
  --container-max: 1280px;
  --prose-max: 768px;

  /* Type scale */
  --fs-eyebrow: 0.75rem;     /* uppercase, letter-spaced */
  --fs-sm:      0.875rem;
  --fs-base:    1rem;
  --fs-lead:    1.125rem;
  --fs-h3:      1.5rem;
  --fs-h2:      clamp(1.875rem, 3vw, 2.5rem);
  --fs-h1:      clamp(2.5rem, 5vw, 4.5rem);
  --lh-tight:   1.15;
  --lh-body:    1.6;
  --tracking-eyebrow: 0.12em;
  --tracking-heading: -0.01em;
}

/* Base */
html { font-family: var(--font-sans); color: var(--color-fg); background: var(--color-bg); }
body { font-size: var(--fs-base); line-height: var(--lh-body); -webkit-font-smoothing: antialiased; }

h1, h2, .display { font-family: var(--font-serif); font-weight: 400; letter-spacing: var(--tracking-heading); line-height: var(--lh-tight); }
h1 { font-size: var(--fs-h1); }
h2 { font-size: var(--fs-h2); }
h3 { font-family: var(--font-sans); font-weight: 600; font-size: var(--fs-h3); }

.eyebrow {
  font-size: var(--fs-eyebrow);
  text-transform: uppercase;
  letter-spacing: var(--tracking-eyebrow);
  font-weight: 600;
  color: var(--color-fg-muted);
}

/* Primary CTA */
.btn-primary {
  background: var(--color-primary);
  color: var(--color-primary-fg);
  font-family: var(--font-sans);
  font-weight: 500;
  padding: 0.75rem 1.5rem;
  border-radius: var(--radius);
  border: 1px solid transparent;
  transition: background 200ms ease, transform 120ms ease;
}
.btn-primary:hover  { background: var(--color-primary-hover); }
.btn-primary:active { transform: translateY(1px); }
.btn-primary:focus-visible { outline: 2px solid var(--color-primary); outline-offset: 2px; }

/* Secondary CTA */
.btn-secondary {
  background: var(--color-surface-alt);
  color: var(--color-fg);
  border: 1px solid var(--color-border);
  border-radius: var(--radius);
  padding: 0.75rem 1.5rem;
  font-weight: 500;
}

/* Card */
.card {
  background: var(--color-surface);
  border: 1px solid var(--color-border);
  border-radius: var(--radius);
  padding: 1.5rem;
}

/* Section container */
.section { padding-block: var(--section-py); }
.container { max-width: var(--container-max); margin-inline: auto; padding-inline: 1.25rem; }
.prose { max-width: var(--prose-max); }

@media (prefers-reduced-motion: reduce) {
  * { animation: none !important; transition: none !important; }
}
```
