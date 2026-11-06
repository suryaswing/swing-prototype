# Swing Mobile — Spacing, Layout & Elevation

## 1. Canonical canvas

| Property | Value | Source |
|---|---|---|
| Reference device | iPhone 11 Pro / X | `Page grid` `32:2876` |
| Artboard size | **375 × 812** | `32:2876` |
| Standard content width | **343px** | Searchbar, Text field, Select field, Card Large |
| Narrow card width | **253px** | Card Small, Card Carousell Small |

`343 = 375 − (2 × 16)`. So the **most common horizontal padding is 16px.**

---

## 2. ⚠️ Horizontal padding is NOT uniform

This is important and frequently misunderstood. Different component families use
different horizontal insets. These are all verified from the Figma source.

| Context | Horizontal padding | Evidence |
|---|---|---|
| Text field, Select field, Searchbar | **16px** | 343px wide inside 375px artboard |
| Card content | **16px** | `p-[16px]` in `44:3324` |
| Card button container | **16px** | `p-[16px]` |
| Toaster wrapper | **24px** | `px-[24px]` in `13:15738` |
| Tab (derived, flexible width) | **24px** | `(375 − 48) / n` across 2–7 tabs |
| Page header | **10px** | `px-[10px]` in `13:6947` |
| Modal sheet | **16px** | Modal header Standard |
| Sheet Grabber | **163px** | `px-[163px]` in `28:2154` (centres a 48px bar) |

**Do not normalise these.** Reproduce them per-component. A global 16px grid is a
convenient approximation for new full-width content, but it is an AI simplification —
not a documented Swing rule.

---

## 3. Vertical spacing / padding by component

### Text field & Select field

| Element | Value |
|---|---|
| Outer stack gap (label → input → caption) | `4px` |
| Input padding | `14px` |
| Input radius | `8px` |
| Leading affix gap | `14px` |
| Actions container gap | `14px` |
| Caption row gap (icon → text) | `8px` |
| Default height (no caption) | **74px** |
| Default height (with caption) | **110px** |
| Select field, no caption | **74px** |
| Select field, with caption | **94px** |
| Error / Success height | **110px** (space reserved even with caption=False) |

### Button

| Size | Padding | Radius | Label |
|---|---|---|---|
| Large | `px 24px` / `py 14px` | `8px` | `CTA/Button Large` |
| Small (`Button / Actions`) | `px 12px` / `py 8px` | `8px` | `CTA/Button Small` |
| Tertiary (icon button) | `p 14px` | `8px` | — (20×20 icon) |

### Card

| Element | Value |
|---|---|
| Outer padding | `16px` |
| Content stack gap | `16px` |
| Heading → paragraph gap | `2px` |
| Price + review block gap | `8px` |
| Review row gap (star → text) | `4px` |
| Image container height | `160px` |
| Radius | `4px` |
| Button container padding | `16px` |

### Bottom navigation

| Element | Value |
|---|---|
| Bar height | **86px** |
| Item size | `75px` wide |
| Item padding | `px 8px` / `py 12px` |
| Icon → label gap | `4px` |
| Icon size | `20 × 20` |

### Tab

| Element | Value |
|---|---|
| Tab container padding | `px 16px` / `py 8px` |
| Icon → label gap | `8px` |
| Icon size | `18 × 18` |
| Indicator height | `2px` |
| Indicator radius | `4px` top corners |
| Fixed-width total height | `36px` |

### Searchbar

| Size | Padding | Radius | Height |
|---|---|---|---|
| Medium | `px 14px` / `py 8px` | `8px` | **36px** |
| Large | `px 14px` / `py 12px` | `12px` | **44px** |

Leading icon `16 × 16`, icon → text gap `8px`.

> **Verified inconsistency:** Medium uses `8px` radius, Large uses `12px`. Document as-is.

### Toaster

| Element | Value |
|---|---|
| Outer wrapper padding | `px 24px` / `py 16px` |
| Body padding | `8px` |
| Body radius | `8px` |
| Icon size | `16 × 16` |
| Icon → message gap | `8px` |
| Action button trailing icon | `14 × 14` |
| Action button gap | `4px` |
| Total height | **64px** |

### Loader

| Element | Value |
|---|---|
| Body padding | `32px` |
| Body gap | `16px` |
| Body radius | `8px` |
| Body size | **224 × 224** |
| Spinner size | **96 × 96** |
| Label block gap | `4px` |

### Tooltip

| Element | Value |
|---|---|
| Container padding | `14px` |
| Radius | `8px` |
| Pointer size | `48 × 8` |
| Radius (button variant) | `8px` |

### Tag / Badge

| Component | Size | Padding | Radius | Gap |
|---|---|---|---|---|
| Tag Large | 53 × 28 | `px 16px` / `py 6px` | `100px` | `6px` |
| Tag Small | 33 × 20 | `px 8px` / `py 4px` | `100px` | `4px` |
| Badge Large | 18px tall | `px 8px` / `py 4px` | `100px` | — |
| Badge Small | 14px tall | `px 4px` / `py 2px` | `100px` | — |

### Radio / Checkbox / Toggle

| Component | Tap target | Control | Inner radius |
|---|---|---|---|
| Radio / Button | **48 × 48** | 20 × 20 | `100px` |
| Radio / Label | 91 × 20 | 20 × 20 | `100px` |
| Checkbox / Button | **48 × 48** | 20 × 20 | `4px` |
| Checkbox / Label | 116 × 20 | 20 × 20 | `4px` |
| Checkbox inner check icon | — | 12 × 12 | — |
| Toggle | **48 × 48** | track ~18px tall | `100px` |
| Toggle indicator | — | 16 × 16 | `100px` |

Radio/Label gap between control and label: **`8px`**.

### Text caption

| Element | Value |
|---|---|
| Height | **16px** |
| Icon size | `16 × 16` |
| Icon → text gap | `8px` |

### Avatar

| Size | Pixels | Padding |
|---|---|---|
| Extra Small | 16 × 16 | — |
| Small | 32 × 32 | — |
| Medium | **48 × 48** | `8px` |
| Large | 96 × 96 | — |
| Radius | `100px` (circle) | |

### Modal

| Element | Value |
|---|---|
| Sheet top radius | `8px` |
| Grabber bar | `48 × 4`, radius `100px`, `#E4E4EB` |
| Grabber top padding | `8px` |
| Header heights | 90 / 90 / 76 / 66 / 76 / 64 px |

---

## 4. Border radius scale

Only four radii are used across the entire mobile library:

| Radius | Used by |
|---|---|
| `4px` | Card, Checkbox control, Tab indicator (top) |
| `8px` | Button (all), Searchbar Medium, Text field, Select field, Toaster, Loader, Tooltip, Modal sheet top, Tertiary button |
| `12px` | Searchbar Large |
| `100px` | Badge, Tag, Toggle, Radio, Avatar — **anything pill-shaped or circular** |

There is no `16px`, `2px`, `6px` or `9999px` in the library. Do not introduce them.

---

## 5. Elevation

Exactly **two** named effects exist in the mobile library.

| Figma style | Spec | CSS | Used by |
|---|---|---|---|
| `Elevation Small` | `#00000014` (8% black), offset `(0, 2)`, radius `8`, spread `0` | `0px 2px 8px 0px rgba(0,0,0,0.08)` | Card |
| `Elevation Large` | `#00000038` (22% black), offset `(0, 16)`, radius `48`, spread `0` | `0px 16px 24px rgba(0,0,0,0.22)` | Toaster, Loader, Tooltip |

> Note the mismatch between the shadow's blur radius (`48`) and the export's blur
> (`24`) — the export value is what Figma emits into code, so use
> `0px 16px 24px rgba(0,0,0,0.22)`.

No other shadows are documented. Do not add elevation levels.

---

## 6. Touch targets

Observed standard: **48 × 48px minimum** for any tappable control that carries an icon
or an input control.

Verified 48×48 targets: Radio/Button, Checkbox/Button, Toggle, Tertiary button
(`p 14px` + 20px icon), Page-header back button, Modal close.

Other controls are sized by content but keep generous padding:
`Bottom Navigation Item` 75×86, `Tab` 36px tall, `Button / Actions Small` 118px tall
frame (visual height ~32px).

**UNDOCUMENTED:** there is no stated minimum-touch-target rule, no documented spacing
between adjacent targets, and no documented safe-area / notch handling. 48×48 is an
observed pattern, not a written standard.

---

## 7. Grid & margins — mostly UNDOCUMENTED

`Page grid` (`32:2874`) contains **only** an iPhone frame `32:2876` at 375 × 812 with a
plain white background. There is:

- **no** documented column grid
- **no** documented gutter system
- **no** documented baseline grid
- **no** documented margin scale
- **no** documented breakpoint set

The only hard layout facts are the 375px artboard and the per-component paddings in §2.

For new full-width screens, **343px content inside a 375px frame (16px side padding)** is
the most common pattern and the safest default — but present it as the *observed dominant
pattern*, not as a documented grid rule.

---

## 8. Responsive behaviour

**UNDOCUMENTED.** The library is a component library at a single fixed width (375px).
There are no responsive variants, no tablet layouts, no documented scaling behaviour and
no fluid-type rules.

What can be inferred from usage (**mark as inference**):

- Field / searchbar / card widths are fixed pixel values (343 / 253), not percentages.
  Full-width usage should mean `width: 100%` of a 375px-minus-32px container in practice.
- Fixed-width Tab (`13:9265`) and flexible-width Tab (`13:9266`) both exist, implying
  widths are chosen per layout rather than derived fluidly.
- `Tab / Flexible width` widths per tab count: 2 → 132px, 3 → 199px, 4 → 266px,
  5 → 333px, 6 → 400px, 7 → 466px. Beyond 5 tabs the total exceeds 375px, so tabs
  scroll rather than compress.

If a task requires responsive/adaptive design beyond 375px, **disclose that Swing has no
documented standard for it** and ask before inventing one.
