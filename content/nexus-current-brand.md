# Nexus Current Brand Standards — Hub Refresh Reference

## Discovery Summary

Searched OneDrive (`Marketing/Brand_Assets/`), live nexusbenefitsolutions.com CSS, the presentations deck builder, and recent client materials. **There is no "2026 brand refresh" — the Forest/Rust/Sage identity with DM Serif Display + DM Sans IS the current Nexus brand.** It's documented in three converging sources: the OneDrive Brand_Assets README, the canonical `brand-guidelines.html` (which Jason maintains), and the deployed CSS at nexusbenefitsolutions.com (compiled HSL values match the brand hex codes exactly — `17 63% 44%` ≈ rust, `150 33% 18%` ≈ deep forest, `60 11% 98%` ≈ natural white).

One file (`design_guidelines.md`) describes a "sophisticated navy gradient identity" — this is **outdated**. It contradicts every other source including the live website, the brand-guidelines.html, and the deck builder assets. Ignore it.

The Cornerstone Well-Being Program hub is **already on-brand** with two minor drift points: a slightly brighter rust (`#C75A2C` vs canonical `#B8522A`) and a slightly cooler parchment (`#FAFAF7` vs `#FAFAF8`). Fonts, mark, and overall identity are correct.

## Canonical Palette

| Token | Hex | Role |
|-------|------|------|
| Deep Forest | `#1F3D2E` | Primary text, headlines, logo, dark surfaces |
| Forest Light | `#2A5240` | Hover, secondary forest accent |
| Rust | `#B8522A` | Primary accent, buttons, links, CTAs |
| Rust Dark | `#9A4422` | Rust hover state |
| Rust Light | `#D4693F` | Rust accent on dark backgrounds |
| Sage | `#7A9282` | Secondary text, borders, tagline |
| Pale Sage | `#E8EBE4` | Card backgrounds, soft surface |
| Natural White | `#FAFAF8` | Page background |
| Charcoal | `#2D2D2D` | Body text alternative |

## Typography

- **Display / Headlines:** `DM Serif Display`, Regular, fallback `Georgia, "Times New Roman", serif`
- **Body / UI:** `DM Sans`, fallback `-apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif`
- **Tagline pattern:** DM Sans Regular, sage color, 0.5px letter-spacing

## Logo Files

Canonical files on local disk:
- `/Users/jasonsmac/Library/CloudStorage/OneDrive-NexusBenefitSolutions/Nexus_Benefit_Solutions/01_Operations_Nexus_SBBMI/Marketing/Brand_Assets/Logos/nexus-logo-forest.svg` — primary forest mark
- `…/Logos/nexus-logo-white.svg` — reversed for dark backgrounds
- `…/Logos/nexus-logo-dark.png` — raster, dark variant
- `…/Logos/nexus-logo-dark-sq.png` — square format
- `…/Logos/nexus-logo-header.png` — header crop

Mark description (from brand-guidelines.html): "The Nexus mark combines a stylized 'N' with an organic leaf element, representing growth, connection, and the natural fit between advisor and client. The circular form suggests completeness and trust." Minimum size: 16px.

## Sample CSS Variables (drop-in replacement)

```css
:root {
  /* Brand colors — canonical */
  --color-fg:            #1F3D2E;  /* Deep Forest */
  --color-fg-muted:      #7A9282;  /* Sage */
  --color-primary:       #B8522A;  /* Rust */
  --color-primary-hover: #9A4422;  /* Rust Dark */
  --color-primary-light: #D4693F;  /* Rust Light (on dark) */
  --color-primary-fg:    #FFFFFF;
  --color-bg:            #FAFAF8;  /* Natural White */
  --color-surface:       #E8EBE4;  /* Pale Sage */
  --color-surface-alt:   #DDE0D3;
  --color-border:        #E8EBE4;
  --color-muted:         #E8EBE4;

  /* Dark surfaces */
  --color-dark-bg:       #1F3D2E;
  --color-dark-fg:       #FAFAF8;
  --color-dark-surface:  #2A5240;

  /* Typography */
  --font-serif: "DM Serif Display", Georgia, "Times New Roman", serif;
  --font-sans:  "DM Sans", -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
}
```

## Side-by-Side: Hub vs Canonical

| Token | Hub today | Canonical | Action |
|-------|-----------|-----------|--------|
| Primary forest | `#1F3D2E` | `#1F3D2E` | ✅ match |
| Primary rust | `#C75A2C` | `#B8522A` | ⚠️ shift to deeper rust |
| Rust hover | `#B8522A` | `#9A4422` | ⚠️ shift darker |
| Page background | `#FAFAF7` | `#FAFAF8` | minor (1 point) — fine |
| Sage muted text | `#5C7066` | `#7A9282` | ⚠️ lighten to match brand |
| Surface | `#E8EADF` | `#E8EBE4` | minor — fine |
| Border | `#D9DDCC` | `#E8EBE4` | ⚠️ shift to pale sage |
| Dark bg | `#0E1F17` | `#1F3D2E` | hub is deeper — keep if for contrast hero |
| Display font | DM Serif Display | DM Serif Display | ✅ match |
| Body font | DM Sans | DM Sans | ✅ match |
| Accent green `#0F7A5C` / teal `#0891B2` / purple `#5B2F8A` | hub-local | not in brand | hub-specific accents — fine to keep for status pills |

## Recommendation

**Light refresh, not a rebuild.** The hub is already 90% on-brand. Apply these three changes:

1. Replace `--color-primary` `#C75A2C` → `#B8522A` (deeper, canonical rust)
2. Replace `--color-primary-hover` `#B8522A` → `#9A4422`
3. Replace `--color-fg-muted` `#5C7066` → `#7A9282` (canonical sage — slightly warmer, more readable on parchment)
4. Optionally bump `--color-border` `#D9DDCC` → `#E8EBE4` for softer card edges

Keep the hub-specific accent greens/teals/purples — they're used for program-status pills and visual differentiation within the hub, not as brand colors. They don't conflict.

**Do not** swap fonts, mark, or core identity. The hub already speaks Nexus.
