# Swing Mobile — Color System

All values below were extracted live from the **ADS: For Mobile** Figma library
(`ILlOBW8RpEBRmDvU6LQsx9`) via Figma MCP. Every hex has a source node recorded.

## 1. The two-tier model

Swing Mobile colors are organised in **two tiers**:

1. **Brand ramp** — `{NAME}/500` (saturated) and `{NAME}/50` (tint).
2. **Neutral ramp** — `DARK/500 → DARK/100` and `LIGHT/500 → LIGHT/100`.

There is **no documented semantic alias layer** (no `color/bg/primary`, no
`surface/raised`, etc.). Components reference ramps directly in Figma. Do not invent
semantic aliases and present them as Swing standards.

---

## 2. Brand ramp

Each family ships a saturated `500` and a tint `50`. Exceptions are noted.

| Family | `500` | `50` | Source node(s) |
|---|---|---|---|
| `PURPLE` | `#5C00E6` | `#F9F3FF` | Tag `13:9058`, Button `11:366`, Avatar `11:689`, Toaster / Other actions `171:6728` |
| `PURPLE / 600` | `#4900B8` | — | Radio pressed fill `13:3732` |
| `PINK` | `#FF00DD` | `#FFF3FC` | Tag `13:9050` |
| `TEAL` | `#00B0E6` | `#F3FAFF` | Tag `13:9040` |
| `ORANGE` | `#FF8113` | `#FFF9EE` | Tag `13:9063`, Toaster / Warning `13:15739` |
| `GREEN` | `#36B37E` | `#EFFFF7` | Tag `13:9036`, Text field / Success `13:3033`, Toaster / Success `13:15740` |
| `RED` | `#FF2A12` | `#FFF8F5` | Tag `13:9051`, Text field / Warning `13:2999`, Toaster / Error `13:15738` |
| `RED / 600` | `#ED1800` | — | Text caption / Error `11:1471` |

`PURPLE / 600` and `RED / 600` are **600-level shades that exist only in the 600 tier** —
there are no 600 levels for the other families in the mobile library.

> **Note on `#f0d`:** Figma's `get_design_context` emits short-form hex inside Tailwind
> arbitrary values. `#f0d` === `#FF00DD`. Always expand before writing CSS.

---

## 3. Neutral ramp

| Token | Hex | Documented role | Source node |
|---|---|---|---|
| `DARK / 500` | `#1C1C28` | Primary text (headings, body, values) | Heading/H5, Body/B2, Radio label `32:2882` |
| `DARK / 400` | `#28293D` | Black Tag border + label; **Tooltip background** | Tag `13:9059`, Tooltip `13:8659` |
| `DARK / 300` | `#555770` | Secondary body text; form field label | Body/B2 paragraph in Card `44:3324`, Text field label |
| `DARK / 200` | `#8F90A6` | Muted/tertiary text, placeholder, Gray Tag, **Toaster / Neutral bg**, Tooltip action icon tint | Text caption `11:1470`, Toaster `13:15737` |
| `DARK / 100` | `#C7C9D9` | Borders; unselected checkbox / radio / toggle-off track | Checkbox `13:3714`, Radio `32:2882`, Toggle `13:3805` |
| `LIGHT / 500` | `#E4E4EB` | Divider / hairline; sheet grabber bar | Divider in Card `44:3324`, Sheet Grabber `28:2153` |
| `LIGHT / 300` | `#F2F2F5` | Searchbar fill; text field fill; select field fill | Searchbar `2160:198`, Text field `13:2994` |
| `LIGHT / 200` | `#FAFAFC` | Image placeholder background; Gray Tag fill | Card image `44:3324`, Tag `177:6984` |
| `LIGHT / 100` | `#FFFFFF` | Surface; white text; White Tag border + label | Button label `11:366`, Toggle indicator |

---

## 4. Semantic color mapping

These are the **only** semantically-named color usages actually present in the library.

### Toaster (5 types — all verified)

| Type | Background | Token | Node |
|---|---|---|---|
| Error | `#FF2A12` | `RED/500` | `13:15738` |
| Warning | `#FF8113` | `ORANGE/500` | `13:15739` |
| Success | `#36B37E` | `GREEN/500` | `13:15740` |
| Neutral | `#8F90A6` | `DARK/200` | `13:15737` |
| Other actions | `#5C00E6` | `PURPLE/500` | `171:6728` |

### Text caption / form field states

| State | Foreground | Background | Border | Node |
|---|---|---|---|---|
| Error / Warning | `#FF2A12` (`RED/500`) | `#FFF8F5` (`RED/50`) | `1px #FF2A12` | `11:1471`, `13:2999` |
| Success | `#36B37E` (`GREEN/500`) | `#EFFFF7` (`GREEN/50`) | `1px #36B37E` | `11:1468`, `13:3033` |
| Neutral | `#8F90A6` (`DARK/200`) | — | — | `11:1470` |

> ⚠️ **Naming trap:** the Text field variant matrix calls the error state **`Warning`**,
> but node `13:2999` uses `RED/500`, not orange. Use red for field errors. The
> `ORANGE/500` warning color is confirmed only on the Toaster and Tag.
>
> **Warning text caption hex is UNVERIFIED** — node `11:1469` was never directly pulled.
> `ORANGE/500 #FF8113` is a **high-confidence inference** from the Toaster, not a
> verified caption value. Treat as inference, never cite as confirmed.

### Focus / selection

| Usage | Value | Node |
|---|---|---|
| Focused input border | `1px #5C00E6` | Text field `13:3005` |
| Active tab label + indicator | `#5C00E6` | Tab `13:9220` |
| Toggle on (track) | `#5C00E6` | Toggle `13:3796` |
| Checkbox selected (fill + border) | `#5C00E6` | Checkbox `13:3721` |
| Radio selected / pressed | `#4900B8` (`PURPLE/600`) | Radio `13:3732` |

> **Inconsistency — document as-is, do not normalise:** Checkbox and Toggle use
> `PURPLE/500`, but Radio uses `PURPLE/600`. This is verified, not a transcription error.

---

## 5. Tag vs Badge — the solid/tint rule

These two components look similar but use **opposite** color strategies. This is the
single most commonly botched pair.

### Tag = **tinted fill** pill

```
bg:     <color>/50
border: 1px solid <color>/500
label:  <color>/500
radius: 100px
```

Verified on Pink Large (`13:9050`):
`bg-[#fff3fc] border border-[#f0d] border-solid ... rounded-[100px]` with label `#f0d`.

Three documented exceptions:

| Tag | Treatment |
|---|---|
| **Black** | No fill. `border 1px solid #28293D` (`DARK/400`) + `#28293D` label. This is the neutral tag. |
| **Gray** | `bg #FAFAFC` (`LIGHT/200`), `border 1px solid #8F90A6`, label `#8F90A6`. |
| **White** | No fill. White border + white label — **only for overlay on imagery**. |

### Badge = **solid fill** pill

```
bg:     <color>/500
border: 1px solid #FFFFFF
label:  #FFFFFF
radius: 100px
```

Verified on Purple Large (`11:914`) and Red Small (`1960:161`).

> An older note claimed Tag was "transparent with outline". That is **REFUTED** —
> Tag is tinted-fill. Only the Black/White tags are unfilled.

---

## 6. Color contrast / accessibility

**UNDOCUMENTED.** The Figma library contains **no** contrast annotations, no WCAG
references, and no documented accessible-pairing rules. Accessibility was not part of
the component documentation.

What is verified and safe to rely on:

- Every solid-fill component in the library pairs its `500` fill with `#FFFFFF` text
  (Button, Badge, Toaster, Avatar, selected Checkbox).
- Tag text uses `<color>/500` on `<color>/50` — these are all light tints, so contrast
  is generally adequate, but **unverified numerically**.
- `DARK/200 #8F90A6` is used for placeholder and muted text on `LIGHT/300 #F2F2F5`
  and `#FFFFFF`. This pair is the lowest-contrast combination in the system and is used
  heavily. **Flag it in review** rather than asserting it passes.

If a design requires a verified contrast ratio, say so explicitly and mark it as an AI
recommendation, not a Swing standard.

---

## 7. Rules for AI agents

1. **Only use hex values from this document.** Every color in a generated design must
   trace to a token above.
2. **Never invent a tint.** If you need `<color>/50` and it is not listed, it does not
   exist — pick a documented token or ask.
3. **Do not invent semantic aliases.** There is no `primary`, `surface`, or `danger`
   token in Swing Mobile. There is `PURPLE/500` and `RED/500`.
4. **Respect the Tag/Badge split.** Tinted for Tag, solid for Badge.
5. **Do not normalise the inconsistencies** (Radio 600 vs Checkbox/Toggle 500,
   Searchbar 8px vs 12px radius, per-component padding). Reproduce reality.
6. `#17352b` and `#2d654d` from `index.html` are **prototype-only**. They are NOT
   design-system colors and must never appear in a Swing Mobile design.
