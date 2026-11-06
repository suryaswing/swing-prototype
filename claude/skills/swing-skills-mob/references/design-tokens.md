# Swing Mobile — Design Tokens (index)

Consolidated index of verified visual foundations and mobile component tokens from
**ADS: Foundations** (`JDN6zpJA4feGSY8ZcQMQeM`) and **ADS: For Mobile**
(`ILlOBW8RpEBRmDvU6LQsx9`). Foundations defines the base visual assets and primitives;
the Mobile library documents how components apply them. Use the topic file for source
and usage rules.

| Topic | File |
|---|---|
| Foundation files, scope, and verified examples | [design-foundations.md](./design-foundations.md) |
| Colour palette & semantics | [color-system.md](./color-system.md) |
| Type scale & named styles | [typography.md](./typography.md) |
| Spacing, layout, radius, elevation | [spacing-layout.md](./spacing-layout.md) |
| Component specs & variant matrices | [components.md](./components.md) |
| States, feedback, motion | [interaction-patterns.md](./interaction-patterns.md) |
| Pre-ship validation | [design-quality-checklist.md](./design-quality-checklist.md) |

---

## 1. Colour tokens — quick reference

### Brand ramp

| Token | Hex | Common semantic |
|---|---|---|
| `PURPLE/700` | `#360087` | Foundation palette; mobile usage not established |
| `PURPLE/500` | `#5C00E6` | Primary action, focus ring, selection, active tab, Avatar bg, Toaster "Other actions" |
| `PURPLE/600` | `#4900B8` | Radio selected fill |
| `PURPLE/300` | `#B284F9` | Foundation palette; mobile usage not established |
| `PURPLE/100` | `#E6DCFA` | Foundation palette; mobile usage not established |
| `PURPLE/50` | `#F9F3FF` | Purple tint surface |
| `PINK/500` | `#FF00DD` | Accent |
| `PINK/50` | `#FFF3FC` | Pink tint surface |
| `TEAL/500` | `#00B0E6` | Info / accent |
| `TEAL/50` | `#F3FAFF` | Teal tint surface |
| `ORANGE/500` | `#FF8113` | Warning |
| `ORANGE/50` | `#FFF9EE` | Orange tint surface |
| `GREEN/500` | `#36B37E` | Success |
| `GREEN/50` | `#EFFFF7` | Green tint surface |
| `RED/500` | `#FF2A12` | Error / destructive |
| `RED/600` | `#ED1800` | Error text emphasis |
| `RED/50` | `#FFF8F5` | Red tint surface |

Foundation-only Purple shades above are verified in `ADS: Foundations` palette `10:229`
(`16:20`, `10:233`, `10:236`, `10:239`, `10:242`). Consult
[design-foundations.md](./design-foundations.md) for node-level detail and verify
component usage in Figma before applying them to Mobile.

### Neutral ramp

| Token | Hex | Semantic |
|---|---|---|
| `DARK/500` | `#1C1C28` | Primary text |
| `DARK/400` | `#28293D` | Tooltip background; Black Tag label/border |
| `DARK/300` | `#555770` | Secondary body text, field labels |
| `DARK/200` | `#8F90A6` | Muted text, placeholder, Toaster Neutral, Gray Tag |
| `DARK/100` | `#C7C9D9` | Borders, unselected controls |
| `LIGHT/500` | `#E4E4EB` | Dividers, hairline, sheet grabber |
| `LIGHT/300` | `#F2F2F5` | Field / searchbar fill |
| `LIGHT/200` | `#FAFAFC` | Image placeholder, Gray Tag fill |
| `LIGHT/100` | `#FFFFFF` | Surface, text on colour |

Full semantics, Tag-vs-Badge rules and contrast notes: [color-system.md](./color-system.md).

---

## 2. Typography tokens — quick reference

**Font family: Manrope only.**

| Style | Size / LH / Tracking | Weight |
|---|---|---|
| `Heading/H5` | 18 / 22 / −0.36px | ExtraBold 800 |
| `Heading/H6` | 14 / 18 / −0.28px | ExtraBold 800 |
| `Body/B1` | 14 / 22 / 0.28px | Regular 400 |
| `Body/B1 Semibold` | 14 / 22 / 0.28px | Bold 700 |
| `Body/B2` | 12 / 20 / 0.24px | Regular 400 |
| `Body/B2 Semibold` | 12 / 20 / 0.24px | Bold 700 |
| `Body/B3 Semibold` | 10 / 16 / 0.20px | Bold 700 |
| `Body/B4 Semibold` | 8 / 12 / 0.16px | Bold 700 |
| `CTA/Button Large` | 16 / 20 / 0.32px | Bold 700 |
| `CTA/Button Small` | 12 / 14 / 0.24px | Bold 700 |
| `Label/Label Small` | 8 / 10 / 0.32px | Bold 700 |
| `Label/Label Large` | 12 / 14 / 0.48px | Bold 700 |

Full scale H1–H6 / S1–S3 / B1–B4: [typography.md](./typography.md).

> **Tracking conversion:** Figma reports `letterSpacing` as a **percentage**.
> `px = size × percent ÷ 100`. The values above are already converted.

---

## 3. Border radius

| Token | Value | Applies to |
|---|---|---|
| `radius/small` | `4px` | Card, Checkbox control, Tab indicator top |
| `radius/medium` | `8px` | Button, Text field, Select field, Searchbar Medium, Toaster, Loader, Tooltip, Modal sheet top, Tertiary button |
| `radius/large` | `12px` | Searchbar Large |
| `radius/pill` | `100px` | Badge, Tag, Toggle, Radio, Avatar |

`radius/small|medium|large` names also exist as FLOAT variables in the sibling
`Eagle - Swing Design System 2.0` library (`Border Radius/border-radius-*`) — values not
retrievable via MCP, but they match the observed `4 / 8 / 12` above.

**No other radii exist in the mobile library.** Do not add `2px`, `6px`, `16px` or `9999px`.

---

## 4. Elevation

| Token | CSS | Applies to |
|---|---|---|
| `Elevation Small` | `0px 2px 8px 0px rgba(0,0,0,0.08)` | Card |
| `Elevation Large` | `0px 16px 24px rgba(0,0,0,0.22)` | Toaster, Loader, Tooltip |

Exactly two. No other shadow tokens are documented.

---

## 5. Spacing values in use

Only these gaps/paddings appear in the mobile library:

`2px` (heading→paragraph) · `4px` (stack gap, icon gaps) · `6px` (Tag Large gap) ·
`8px` (body gaps, caption gap, control→label) · `10px` (page-header side padding) ·
`12px` (button small py, nav item py) · `14px` (input padding, icon-button padding,
leading affix gap) · `16px` (card padding, tab px) · `24px` (button large px,
toaster side padding) · `32px` (loader padding) · `163px` (grabber centring)

There is **no documented 4pt/8pt spacing scale** and no spacing token names exposed
through the mobile library. Treat these as observed values, not a published scale.
Details: [spacing-layout.md](./spacing-layout.md).

---

## 6. Size tokens

| Token | Value |
|---|---|
| Artboard width | `375px` |
| Artboard height | `812px` |
| Content width | `343px` |
| Narrow card width | `253px` |
| Min tap target | `48 × 48px` |
| Bottom nav height | `86px` |
| Page header height | `48px` |
| Tab height | `36px` |
| Button (large) height | `~48px` (14px py + 20px line) |
| Text field height | `74px` (110px with caption) |
| Select field height | `74px` (94px with caption) |
| Searchbar Medium / Large | `36px` / `44px` |
| Toaster height | `64px` |
| Loader body | `224 × 224` |
| Loader spinner | `96 × 96` |

---

## 7. Icon tokens

Namespace convention `namespace/name`:

- `interface/<name>` — standard UI icons
- `interface/so-<name>` — Swing-original (filled/branded) icons
- `arrow/<name>` — directional
- `Logo / <name>` — brand marks

Observed sizes: `10 / 12 / 14 / 16 / 18 / 20 / 48` px, chosen per context.
See [components.md](./components.md) §20 for the context→size mapping.
For asset selection, logo protection, per-screen asset manifests, and stable code exports,
follow [icon-logo-usage.md](./icon-logo-usage.md). The verified `Logo / Swing Pass icon`
is node `912:14146` (20 × 20px within `Swing Pass`, `912:14145`); it is not a general
Swing wordmark.

---

## 8. Token sources — where the truth lives

| Source | Key | Notes |
|---|---|---|
| **`ADS: Foundations`** | Figma file `JDN6zpJA4feGSY8ZcQMQeM` | **Authoritative for foundational palette, elevation, icon, and brand/logo assets.** |
| **`ADS: For Mobile`** | Figma file `ILlOBW8RpEBRmDvU6LQsx9` | **Authoritative for mobile components, layout, and interaction specifications.** Variable collection named `Collection` |
| `Eagle - Swing Design System 2.0` | sibling library | Structural tokens only: `Font & Typefaces/Font`, `Font & Typefaces/DIsplay & Header Spacing`, `Border Radius/border-radius-{small,medium,large}`. Contains `Desktop / Button`, `Mobile / Button` |
| `ADS: For Desktop` | sibling library | **Do not use for mobile** |
| `Minimal_Web` | sibling library | **Do not use for mobile** |

### Not retrievable via MCP

`get_variable_defs` requires an **active selection in the Figma desktop app** and fails
headlessly. The complete variable system (variable collection names, modes, aliases) is
therefore **NOT DOCUMENTED** here. Everything above was extracted from component node
properties and the named-style lists that `get_design_context` returns.

| Token category | Status |
|---|---|
| Colour values | **VERIFIED** from component fills/strokes/text |
| Type styles | **VERIFIED** — named styles with font/size/LH/tracking |
| Radius values | **VERIFIED** from observed geometry |
| Shadow values | **VERIFIED** — two named effect styles |
| Spacing tokens | **OBSERVED** — no named scale found |
| Semantic aliases (e.g. `color.action.primary`) | **UNDOCUMENTED** — do not invent names |
| Modes / theming / dark mode | **UNDOCUMENTED** |
| Token variable IDs | **NOT RETRIEVABLE** |
