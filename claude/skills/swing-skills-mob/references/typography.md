# Swing Mobile — Typography

Extracted from the **Typography** page (`0:1`) of the **ADS: For Mobile** library
(`ILlOBW8RpEBRmDvU6LQsx9`).

## 1. Font family

**Manrope** is the only typeface used across the entire mobile library. Weight `800`
(ExtraBold) is used for headings; `700` (Bold) for CTAs, labels and inline emphasis;
`400` (Regular) for body copy.

> **UNDOCUMENTED:** there is no documented fallback stack, no `font-family` CSS var
> exposed through the mobile library, and no documented `@font-face`/loading strategy.
> A sibling library (`Eagle - Swing Design System 2.0`) exposes `Font & Typefaces/Font`
> as a STRING variable, but its value was not retrievable via MCP (see §7).
> Recommended fallback if you must write CSS: `Manrope, system-ui, sans-serif` —
> **this is an AI recommendation, not a Swing standard.**

---

## 2. Three type systems

The Typography page documents three independent modular scales:

| System | Frame | Font scale | Line-height scale | Base size |
|---|---|---|---|---|
| **Headings** | `2:162` | 1.20 (Minor Third) | 1.25 (Major Third) | 36px (H1) |
| **Subheadings** | `2:194` | 1.125 (Major Second) | 1.414 (Augmented Fourth) | 18px (S1) |
| **Body** | `2:219` | 1.200 (Minor Third) | 1.618 (Golden Ratio) | 14px (B1) |

---

## 3. The scale

| Style | Font | Weight | Size | Line height | Letter spacing |
|---|---|---|---|---|---|
| H1 | Manrope ExtraBold | 800 | 36px | 46px | −0.72px |
| H2 | Manrope ExtraBold | 800 | 30px | 38px | −0.60px |
| H3 | Manrope ExtraBold | 800 | 24px | 30px | −0.48px |
| H4 | Manrope ExtraBold | 800 | 20px | 24px | −0.40px |
| H5 | Manrope ExtraBold | 800 | 18px | 22px | −0.36px |
| H6 | Manrope ExtraBold | 800 | 14px | 18px | −0.28px |
| S1 Semibold | Manrope Bold | 700 | 18px | 26px | 0 |
| S1 Regular | Manrope Regular | 400 | 18px | 26px | 0 |
| S2 | Manrope Regular | 400 | 16px | 22px | 0 |
| S3 | Manrope Regular | 400 | 14px | 20px | 0 |
| B1 Semibold | Manrope Bold | 700 | 14px | 22px | 0.28px |
| B1 | Manrope Regular | 400 | 14px | 22px | 0.28px |
| B2 Semibold | Manrope Bold | 700 | 12px | 20px | 0.24px |
| B2 | Manrope Regular | 400 | 12px | 20px | 0.24px |
| B3 Semibold | Manrope Bold | 700 | 10px | 16px | 0.20px |
| B3 | Manrope Regular | 400 | 10px | 16px | 0.20px |
| B4 Semibold | Manrope Bold | 700 | 8px | 12px | 0.16px |
| Type@96 | Manrope Regular | 400 | 16px | 20px | 0 |
| Type@59 | Manrope Regular | 400 | 12px | 14px | 0 |

---

## 4. Named text styles (exact Figma definitions)

These are the styles actually applied to components. **Use these first** — they are the
authoritative set. The `letterSpacing` value below is what Figma reports; the px column
is the resolved value you write in CSS.

| Figma style name | Font | Size | LH | Figma `letterSpacing` | → CSS px |
|---|---|---|---|---|---|
| `Heading/H1` | Manrope ExtraBold 800 | 36 | 46 | −2 | −0.72px |
| `Heading/H2` | Manrope ExtraBold 800 | 30 | 38 | −2 | −0.60px |
| `Heading/H3` | Manrope ExtraBold 800 | 24 | 30 | −2 | −0.48px |
| `Heading/H4` | Manrope ExtraBold 800 | 20 | 24 | −2 | −0.40px |
| `Heading/H5` | Manrope ExtraBold 800 | 18 | 22 | −2 | −0.36px |
| `Heading/H6` | Manrope ExtraBold 800 | 14 | 18 | −2 | −0.28px |
| `Body/B1` | Manrope Regular 400 | 14 | 22 | 2 | 0.28px |
| `Body/B1 Semibold` | Manrope Bold 700 | 14 | 22 | 2 | 0.28px |
| `Body/B2` | Manrope Regular 400 | 12 | 20 | 2 | 0.24px |
| `Body/B2 Semibold` | Manrope Bold 700 | 12 | 20 | 2 | 0.24px |
| `Body/B3 Semibold` | Manrope Bold 700 | 10 | 16 | 2 | 0.20px |
| `Body/B4 Semibold` | Manrope Bold 700 | 8 | 12 | 2 | 0.16px |
| `CTA/Button Large` | Manrope Bold 700 | 16 | 20 | 2 | 0.32px |
| `CTA/Button Small` | Manrope Bold 700 | 12 | 14 | 2 | 0.24px |
| `Label/Label Small` | Manrope Bold 700 | 8 | 10 | 4 | 0.32px |
| `Label/Label Large` | Manrope Bold 700 | 12 | 14 | 4 | 0.48px |

### ⚠️ The letterSpacing trap — read this before writing any CSS

Figma's `letterSpacing` in the design-context style list is a **PERCENTAGE**, not pixels.
The naive reading (`-2px` on an 18px heading) produces catastrophically wrong tracking.

```
px = size × percent ÷ 100
```

- `Heading/H5`: 18 × −2 ÷ 100 = **−0.36px**
- `Body/B1`: 14 × 2 ÷ 100 = **0.28px**
- `Label/Label Large`: 12 × 4 ÷ 100 = **0.48px**

All the "→ CSS px" values in the table above already apply this formula.

---

## 5. Where each style is used

Learned from inspecting the components. Use this to pick the right style without guessing.

| Style | Used for | Example node |
|---|---|---|
| `Heading/H5` | Screen/section titles; Card heading | Page header title `13:6947`, Card `44:3324` |
| `Heading/H6` | Tab labels; compact headings | Tab item `13:9220` |
| `Body/B1 Semibold` | Tooltip label; form field label; Loader line 2 | Tooltip `13:8659`, Select field label `11:1737` |
| `Body/B1` | Body copy; Loader line 1 | Loader `726:13796` |
| `Body/B2` | Input value / placeholder; Select option; Radio label | Text field `13:2994`, Radio `32:2882` |
| `Body/B2 Semibold` | Leading input affix (e.g. "Rp.") | Text field Label leading `13:2974` |
| `Body/B3 Semibold` | Text caption; Tag label; Bottom nav label; Toaster message | Text caption `11:1471`, Tag `13:9058`, Toaster `13:15738` |
| `Body/B4 Semibold` | Small Tag label | Tag Small `914:14139` |
| `CTA/Button Large` | Button label, Large size | Button `11:366` |
| `CTA/Button Small` | Button label, Small size; Toaster action | Button Actions `44:2640`, Toaster `13:15738` |
| `Label/Label Small` | Badge label | Badge `11:914` |
| `Label/Label Large` | Avatar initials | Avatar `11:689` |

---

## 6. Hierarchy guidance

Derived from observed usage (**not** a documented rule set — treat as inference where
it goes beyond the table in §5):

- **Screen title** → `Heading/H5` (18/22, ExtraBold, `#1C1C28`)
- **Card heading** → `Heading/H5`
- **Section heading** → `Heading/H6` (14/18) or `Body/B1 Semibold`
- **Body / description** → `Body/B2` (12/20) in `#555770`, or `Body/B1` (14/22)
- **Field label** → `Body/B1 Semibold` in `#555770`
- **Input value / placeholder** → `Body/B2`
- **Helper / caption text** → `Body/B3 Semibold` in `#8F90A6`
- **Button label** → `CTA/Button Large` (large) / `CTA/Button Small` (small)
- **Metadata (badge, tag)** → `Label/Label Small` / `Body/B3 Semibold`

---

## 7. Undocumented / gaps

| Item | Status |
|---|---|
| Font fallback stack | **UNDOCUMENTED** |
| Font loading strategy / `@font-face` | **UNDOCUMENTED** |
| Minimum body size rule | **UNDOCUMENTED** — the scale reaches 8px (`Body/B4`, `Label/Label Small`), which is used for Badge and small Tag labels |
| Maximum line length / measure | **UNDOCUMENTED** |
| Line-height tightening on mobile breakpoints | **UNDOCUMENTED** |
| Variable-collection font token value | **NOT RETRIEVABLE** — `get_variable_defs` requires a live Figma selection |
| Text truncation / max-lines behaviour | **UNDOCUMENTED** |

If a task depends on any of these, disclose the gap and ask — do not invent a standard.
