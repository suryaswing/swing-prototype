# Swing Mobile — Component Library

Every component, variant matrix, exact geometry and source node ID, extracted live from
**ADS: For Mobile** (`ILlOBW8RpEBRmDvU6LQsx9`).

**Rule: reuse these whenever they fit.** New component and interaction-pattern proposals
are allowed when no existing component or established Swing pattern meets the need, within
the approximately 30% novelty allowance in `SKILL.md` §5. New proposals are not official
Swing standards until approved and documented.

---

## 1. Button

**Page `6:3`** · families: `Button / Actions`, `Button / Destructive`, `Button / Tertiary`

### `Button` — main matrix (`6:3`), 128 variants

| Prop | Values |
|---|---|
| `Type` | Primary, Secondary, Subtle, Link |
| `State` | Default, On press, Loading, Disabled |
| `Icon` | No icon, On the left, On the right, Icon only |
| `Size` | Large, Small |

4 × 4 × 4 × 2 = **128 variants**.

### Geometry

| Recipe | Node | Spec |
|---|---|---|
| Primary / Large / Default / No icon | `11:366` | `bg #5C00E6`, `px 24px`, `py 14px`, `rounded 8px`, content centred, `cursor: pointer`. Label `CTA/Button Large` (Manrope Bold 16/20, tracking 0.32px) in `#FFFFFF` |

### `Button / Actions` — the workhorse (`45:3237`)

28 variants: `Size` (Small `167.5×118`, Medium `253×118`) × `State` (Default, On press) ×
`Color` (**Purple, Pink, Green, Orange, Teal, Red, Gray**) = 28.

**Small / Default / Purple** (`44:2640`):
```
bg #5C00E6 · px 12px · py 8px · rounded 8px
display: flex · gap 4px · align-items center · justify-content center
label: CTA/Button Small (Manrope Bold 12/14, tracking 0.24px) #FFFFFF
trailing icon (optional): 14 × 14
```

### `Button / Tertiary` — icon button

```
display: flex · align-items center · justify-content center
padding: 14px · border-radius: 8px · cursor: pointer
icon: 20 × 20   → effective tap target 48 × 48
```

Three documented uses:
1. Page-header back button (`13:6947`)
2. Tooltip trailing dismiss (`13:8656`, icon `interface/close-lg`, tinted `DARK/200`)
3. Inline text action inside Toaster — `flex gap 4px`, label `CTA/Button Small` white,
   icon `14 × 14`

### Reuse rule

`Button / Actions` is the correct choice for card actions, form actions and inline
buttons. `Button` (Primary/Secondary/…) is for full-width or prominent CTAs. Tertiary is
**icon-only** — do not use it for text buttons.

---

## 2. Text field

**Page `11:923`** · matrix `13:3034` — **56 variants**, width **343px** for all.
(`Text field 2` on page `2083:2677` is a newer generation — **NOT YET DOCUMENTED**.)

Sub-sections: `Simple` (`12:247`), `Label leading` (`13:1916`), `Label trailing`
(`13:1987`), `Area` (`58:8828`), `Comment` (`143:4911`), `Chat` (`148:5832`),
`Trailing selector` (`12:300`), `Leading selector` (`13:1425`), `Actions` (`13:1519`).

`State` (Default, Focused, Typing, Completed, Disabled, Warning, Success) ×
`Type` (Simple, Label leading, Label trailing, Actions) × `Text caption` (False, True).

### Anatomy

```
outer:  flex column · gap 4px · align-items start · width 343px
  label:   Body/B1 Semibold · #555770        (optional, sits above input)
  input:   flex · align-items center · padding 14px · radius 8px · width 100%
  caption: flex · gap 8px · align-items center   (optional)
```

Placeholder / value text: `Body/B2`.

### State table

| State | Node | Input spec | Text color |
|---|---|---|---|
| Default | `13:2994` | `bg #F2F2F5`, no border | placeholder `#8F90A6` |
| Focused | `13:3005` | `bg #F2F2F5`, `border 1px solid #5C00E6` | — |
| Disabled | `13:2973` | `bg #F2F2F5`, no border | value `#8F90A6` |
| Warning / Error | `13:2999` | `bg #FFF8F5`, `border 1px solid #FF2A12` | placeholder `#FF2A12` |
| Success | `13:3033` | `bg #EFFFF7`, `border 1px solid #36B37E` | value `#1C1C28` |

Error / Success captions: icon `interface/so-warning-circle` / `interface/so-tick-circle`
(16×16) + `Body/B3 Semibold` text in the matching color.

### Structural variants

| Variant | Node | Spec |
|---|---|---|
| Label leading | `13:2974` | input `flex gap 14px align-items center`, leading label `Body/B2 Semibold` `#8F90A6` (e.g. "Rp.") |
| Actions | `13:3032` | input `flex justify-between`; `Actions Container` = `flex gap 14px cursor-pointer` holding 1–2 `Button / Actions` |
| Caption = True | `13:3022` | Default input + caption row: `interface/info` 16×16 + `Body/B3 Semibold` `#8F90A6` |

---

## 3. Select field

**Page `11:1161`** · `Select field` (`11:1745`) — 12 variants, all **343px**.
`State` (Default, Active, Selected, Disabled, Error, Success) × `Text caption` (False, True).

| Measurement | Value |
|---|---|
| Default / Selected / Disabled, no caption | 74px |
| With caption | 94px |
| Active (dropdown open) | 276px |
| Error / Success | 94px |

**Selected + caption (`11:1737`)** — full anatomy:
```
outer:  flex column · gap 4px · align-items start · width 343px
  label: Body/B1 Semibold · #555770
  input: bg #F2F2F5 · flex · align-items center · justify-content space-between
         padding 14px · radius 8px · width 100%
    value: Body/B2 · #1C1C28
    trailing: arrow/chevron-down · 20 × 20
  caption: flex · gap 8px · align-items center · width 139px
    interface/info 16 × 16 + Body/B3 Semibold · #8F90A6
```

`Select option` (`11:1261`): 18 variants, all **343 × 36**.
`State` (Default, On press, Disabled) × `Front component` (None, Icon, Checkbox) ×
`Supporting text` (False, True).

Key nodes: Default+None+False `11:1260` · Default+Icon+False `11:1256` ·
Default+Checkbox+False `13:15529` · On press+None+False `11:1257` ·
Disabled+None+False `11:1259` · Default+None+True `11:1314`.

> `Select field 2` (`2083:86`) exists — **NOT YET DOCUMENTED**.

---

## 4. Radio

**Page `13:3727`** — two families.

### `Radio / Button` (`13:3728`) — 6 variants, each **48 × 48**

`Status` (True, False) × `State` (Default, On press, Disabled)

```
container: size 20 × 20 · border-radius 100px
  unselected: bg #FFFFFF · border 1px solid #C7C9D9
  selected:   bg #4900B8  (PURPLE/600)
outer tap target: 48 × 48 (padding 14px)
```

Nodes: True/Default `13:3729` · True/On press `13:3732` · True/Disabled `13:3785` ·
False/Default `13:3747` · False/On press `13:3749` · False/Disabled `13:3783`.

### `Radio / Label` (`32:2881`) — 6 variants, each **91 × 20**

```
flex · gap 8px · align-items center · justify-content center
container 20 × 20 (same styling as above)
label: Body/B2 · #1C1C28
```

Nodes: True/Default `32:2882` · True/On press `32:2885` · True/Disabled `32:2888` ·
False/Default `32:2891` · False/On press `32:2893` · False/Disabled `32:2895`.

---

## 5. Checkbox

**Page `13:3521`** — two families.

### `Checkbox / Button` (`13:3722`) — 9 variants, each **48 × 48**

`Status` (Selected, Indeterminate, Unselected) × `State` (Default, On press, Disabled)

```
box: 20 × 20 · border 1px solid · border-radius 4px
  unselected: bg #FFFFFF · border #C7C9D9
  selected:   bg #5C00E6 · border #5C00E6 · padding 4px
              with 12 × 12 interface/so-checkmark icon
```

Nodes: Unselected/Default `13:3714` · Selected/Default `13:3721`.

### `Checkbox / Label` (`32:2902`) — 9 variants, each **116 × 20**

Same 3 × 3 matrix, label to the right, 20 × 20 box.

---

## 6. Toggle

**Page `13:3794`** · `Toggle` (`13:3795`) — 4 variants, each **48 × 48**
(`flex align-items center justify-content center`, `px 8px py 15px`).

`Status` (True, False) × `State` (Default, Disabled)

```
track:     height ≈ 18px · border-radius 100px
indicator: bg #FFFFFF · border-radius 100px · 16 × 16
  off (13:3805): bg #C7C9D9 · indicator left
  on  (13:3796): bg #5C00E6 · indicator right
```

---

## 7. Search bar

**Page `32:2352`** · `Searchbar` (`32:2467`) — 10 variants.
`State` (Default, Focused, Typing, Completed, Disabled) × `Size` (Medium `343×36`,
Large `343×44`).

| Size | Node | Spec |
|---|---|---|
| Large / Default | `2160:198` | `bg #F2F2F5`, `flex gap 8px align-items center`, `px 14px py 12px`, `radius 12px`, `width 343px` |
| Medium / Default | `32:2466` | same but `py 8px`, `radius 8px` |

Leading icon `16 × 16` (`interface/search` `515:7044`). Placeholder `Body/B2` `#8F90A6`.

---

## 8. Card

**Page `11:922`** · families: `Card / Standard`, `Card / Carousell`,
`Card / Highlighted scorecard`, `Golf Course Card / New`.

### `Card / Standard` (`44:3325`)

`Size` (Small `253×356`, Large `343×356`) × `Image position` (Top, Middle, Bottom,
Full screen), plus `Top New` (Small `253×423`, Large `343×423`).

**Small / Image position = Top** (`44:3324`):
```
bg #FFFFFF · radius 4px · width 253px · flex column · overflow: clip
box-shadow: 0px 2px 8px 0px rgba(0,0,0,0.08)   /* Elevation Small */

image container: height 160px · placeholder bg #FAFAFC
                 centred interface/so-image 48 × 48

content: flex column · gap 16px · padding 16px
  heading:   Heading/H5 (Manrope ExtraBold 18/22, tracking -0.36px) · #1C1C28
  paragraph: Body/B2 (12/20, tracking 0.24px) · #555770   ← gap 2px from heading
  price + review block: gap 8px
    badge: bg #36B37E · border 1px solid #FFFFFF · px 8px py 4px · radius 100px
           label: Label/Label Small (Manrope Bold 8/10, tracking 0.32px) · #FFFFFF
    "Available today": Manrope Bold 8/10 · #8F90A6
  review row: gap 4px
    interface/so-stars 16 × 16 (node 1962:92)
    Body/B3 Semibold · #8F90A6

divider: hairline #E4E4EB
button container: padding 16px · containing Button / Actions (Small)
```

### Other card families

| Family | Node | Variants |
|---|---|---|
| `Card / Carousell` | `45:2692` | Large `343×240`, Small `253×240` |
| `Card / Highlighted scorecard` | `159:7746` | `Type` (Image background, Solid color background, Empty) × `Description` (True, False) → `253×356` / `253×306` |
| `Golf Course Card / New` | `914:14751` | `Size` (Large `327×414`, Medium `253×414`, Small `155.5×234`) × `Price Type` (Publish, Special rate) = 6 |

---

## 9. Badge

**Page `11:833`** · `Badge` (`11:918`) — **64 variants**.
`Color` (Purple, Orange, Green, Teal, Pink, Black, Gray, Red) × `Content` (Label only,
Label + icon, Icon only, Indicator) × `Size` (Large, Small).

| Size | Height | Label only | Label + icon | Icon only | Indicator |
|---|---|---|---|---|---|
| Large | 18px | 44 × 18 | 58 × 18 | 18 × 18 | 8 × 8 |
| Small | 14px | 36 × 14 | 46 × 14 | 14 × 14 | 4 × 4 |

**Solid fill** (unlike Tag):
```
Purple / Label only / Large (11:914):
bg #5C00E6 · border 1px solid #FFFFFF · px 8px py 4px · radius 100px
label: Label/Label Small · #FFFFFF

Red / Label only / Small (1960:161):
bg #FF2A12 · border 1px solid #FFFFFF · px 4px py 2px · radius 100px
label: Label/Label Small
```

> **Same 8px label in both sizes** — only the padding and container differ.

---

## 10. Tag

**Page `13:8662`** · `Tag` (`13:9065`) — **54 variants**.
`Color` (Black, Purple, Pink, Teal, Orange, Green, Red, Gray, White) ×
`State` (Default, Focused, Default (Transparent)) × `Size` (Large, Small).

| Size | Dimensions | Padding | Gap | Label style |
|---|---|---|---|---|
| Large | 53 × 28 | `px 16px py 6px` | `6px` | `Body/B3 Semibold` |
| Small | 33 × 20 | `px 8px py 4px` | `4px` | `Body/B4 Semibold` |

**Tinted fill** (opposite of Badge):
```
bg <color>/50 · border 1px solid <color>/500 · radius 100px
label <color>/500
```

Exceptions: **Black** = no fill, `border 1px solid #28293D`, label `#28293D`.
**Gray** = `bg #FAFAFC`, `border 1px solid #8F90A6`, label `#8F90A6`.
**White** = no fill, white border + white label (overlay on imagery only).

Optional slots:
- `hasIcon` → `interface/so-love` `12×12` (Small `10×10`)
- `hasBadge` → nested Badge (`bg #FF2A12`, `px 4px py 2px`, `radius 100px`, border white)
- `removable` → `interface/close-circle` `12×12`
- `infoIcon` → `interface/info` `12×12`

Node IDs — Large: Black `13:9059`, Purple `13:9058`, Pink `13:9050`, Teal `13:9040`,
Orange `13:9063`, Green `13:9036`, Red `13:9051`, Gray `177:6984`, White `1605:14539`.
Small: `914:14139` (Black) … `914:14231` (Gray).

---

## 11. Text caption

**Page `11:1442`** · `Text caption` (`11:1472`) — 4 variants, each **16px** tall.
`Type` (Error, Warning, Success, Neutral), leading icon `16 × 16`, label `Body/B3 Semibold`.

| Type | Node | Icon | Color |
|---|---|---|---|
| Error | `11:1471` | `interface/so-warning-circle` | `#FF2A12` |
| Success | `11:1468` | `interface/so-tick-circle` | `#36B37E` |
| Neutral | `11:1470` | `interface/info` | `#8F90A6` |
| Warning | `11:1469` | — | **UNVERIFIED** — see color-system.md §4 |

---

## 12. Navigation — Bottom Navigation

**Page `13:9387`** · `Bottom Navigation` (`2266:42`) — `Type` = `3 items` / `4 items`,
both **375 × 86**.

`Bottom Navigation Item` (`13:9463`):
```
flex column · gap 4px · align-items center · justify-content center
px 8px py 12px · width 75px
icon:  20 × 20
label: Body/B3 Semibold (Manrope Bold 10/16, tracking 0.2px) · #1C1C28 · centred
```

Item matrix: `Type` (Home, Feed, Activities, Chats, Friends, Account, Feed post,
Default) × `State` (Default, Focused) × `Notification badge` (True, False) = 32 variants.

---

## 13. Tab

**Page `13:9130`** · matrix `13:9221` — 8 variants.
`State` (Default, Focused) × `Icon` (True, False) × `Size` (Large `91–117×36`,
Small `77–95×34`).

**Focused + icon + large** (`13:9220`):
```
container: flex · gap 8px · align-items center · justify-content center
           px 16px py 8px
icon: 18 × 18
label: Heading/H6 (Manrope ExtraBold 14/18, tracking -0.28px)
indicator: bg #5C00E6 · height 2px · border-radius 4px 4px 0 0 · full width
```

**Default, no icon, large** (`13:9217`): container `bg #FFFFFF`; tab `px 16px py 8px`;
label `#1C1C28`; indicator `bg #FFFFFF` height 2px. Focused swaps label + indicator
to `#5C00E6`.

| Set | Node | Widths |
|---|---|---|
| `Tab / Fixed width` | `13:9265` | 2, 3, 4 tabs — each **375 × 36** |
| `Tab / Flexible width` | `13:9266` | 2 → 132px, 3 → 199px, 4 → 266px, 5 → 333px, 6 → 400px, 7 → 466px (all × 36) |

---

## 14. Page header

**Page `13:6886`** · families: `Standard` (`13:6950`), `Home` (`42:2318`),
`Home Public` (`912:14100`), `Activities` (`93:4680`), `Chats` (`220:7048`),
`Explore` (`234:7056`).

**Standard** — `Type` (Title only, Single label button, Double label button,
Single icon button, Double icon button) × `Title placement` (Left, Middle) = **10
variants**, all **375 × 48**.

**Standard / Title only / Left** (`13:6947`):
```
bg #FFFFFF · flex column · align-items start · justify-content center
px 10px · width 375px
back button: Button / Tertiary — padding 14px, radius 8px, 20 × 20 icon (48 × 48 target)
title: Heading/H5 · #1C1C28
```

Other families: `Home` (`Notification` T/F, 375×48) · `Home Public`
(`Notification` × `Swing Pass`, 375×48) · `Chats` (`Type` = Chats 375×64, Group chats
375×48, Personal chat 375×48, Search 375×100) · `Explore` (`Filter status` T/F).

`Swing Pass` sub-component (`912:14145`): `76 × 28`, `20 × 20` `Logo / Swing Pass icon`
+ `PASS` text `36 × 18`.

---

## 15. Modal

**Page `13:15747`**

| Component | Node | Variants |
|---|---|---|
| `Modal header / Standard` | `13:15994` | `Content` (Title + description, Title only, Description only) × `Actions` (True, False) = 6, width 375. Heights 90 / 90 / 76 / 66 / 76 / 64 |
| `Sheet Grabber` | `28:2154` | `bg #FFFFFF`, `flex column align-items center justify-content center`, `pt 8px px 163px`, `radius 8px 8px 0 0`, `width 375px`. Bar (`28:2153`): `bg #E4E4EB`, `radius 100px`, **48 × 4** |
| `Modal content` | `26:3939` | 375 × 232 |
| `Modal / Content` | `28:2443` | `Button` × `Keyboard` = 4, each 375 × 750 |
| `Modal / Dialog` | `28:2447` | `Image` (True, False) → 375 × 548 / 375 × 432 |
| `Modal header / Actions` | `62:9392` | `Action type` (Searchbar, Tags, Searchbar + Tags) × `Content` (No title, Title only, Title + Action) = 7 |
| `Modal / List` | `101:4840` | `Additional text` × `Header` = 4 |
| `Modal / Share` | `1911:12058` | `State` (Default, Focused, Search result, Select, No result) = 5, each 375 × 750 |

Detail specs for modal interiors are **NOT YET FULLY DOCUMENTED**.

---

## 16. Tooltip

**Page `13:6985`** (page name is misspelled `Tootip` in Figma) ·
`Tooltip / Standard` (`13:8661`) — `Position` (Top, Bottom, Left, Right) ×
`Button` (True, False) = **8 variants**.

Sizes: Bottom/False `13:8660` 66×58 · Top/False `13:8659` 66×58 · Right/False `13:8658`
74×50 · Left/False `13:8654` 74×50 · Right/True `13:8655` 108×48 · Left/True `13:8657`
108×48 · Bottom/True `13:8653` 100×56 · Top/True `13:8656` 100×56.

```
container: bg #28293D (DARK/400) · flex align-items center justify-content center
           overflow clip · padding 14px · radius 8px
label: Body/B1 Semibold · #FFFFFF
shadow: Elevation Large

Button=True variant: container pl 14px + trailing Button / Tertiary
  (padding 14px, radius 8px, 20 × 20 interface/close-lg, cursor pointer, tint DARK/200)

pointer: 48 × 8 triangle, rotate 180 for Top position, inset 0 33.33%
```

Figma component descriptions exist for this component only — e.g.
"tooltip, simple, top, helper, top pointer".

`Tooltip / Map` (`944:14804`): `State` (Default `944:14803`, Active `944:14802`),
each **78 × 40**.

---

## 17. Toaster

**Page `13:15471`** · `Toaster` (`13:15741`) — 5 variants, all **375 × 64**.

| Type | Node | Background | Icon |
|---|---|---|---|
| Error | `13:15738` | `#FF2A12` | `interface/so-warning-circle` |
| Warning | `13:15739` | `#FF8113` | `interface/warning-circle` |
| Success | `13:15740` | `#36B37E` | `interface/so-tick-circle` |
| Neutral | `13:15737` | `#8F90A6` | `interface/so-info` |
| Other actions | `171:6728` | `#5C00E6` | `interface/so-info` |

```
wrapper: flex column · align-items center · justify-content center
         px 24px py 16px · width 375px

body: flex · gap 8px · align-items center · justify-content center
      padding 8px · radius 8px · width 100% · shadow Elevation Large
  icon: 16 × 16
  message: flex column · flex 1 · Body/B3 Semibold · #FFFFFF · line-height 16px
  action (optional): Button / Tertiary — flex gap 4px · radius 8px · cursor pointer
      label CTA/Button Small #FFFFFF + trailing icon 14 × 14   (e.g. "See my cart")
```

---

## 18. Loader

**Page `726:13639`** · `Loader` (`726:13797`) — `Label` × `Percentage` = **4 variants**,
all **224 × 224**.

Nodes: Label=T/Percentage=T `726:13796` · Label=F/Percentage=T `726:13795` ·
Label=T/Percentage=F `726:13793` · Label=F/Percentage=F `726:13794`.

```
body: bg #FFFFFF · shadow Elevation Large · flex column · gap 16px
      align-items center · justify-content center
      padding 32px · radius 8px · size 224 × 224
  spinner: 96 × 96
  label block (726:13772): flex column · gap 4px · align-items center · text-center
    width 100% · color #1C1C28 · 14px · tracking 0.28px
    line 1: Body/B1          (e.g. "Fetching data...")
    line 2: Body/B1 Semibold (e.g. "50%")
```

---

## 19. Avatar

**Page `11:612`** · `Avatar / Single` (`11:690`) — `Type` (Initials, Guest, Pictures) ×
`Size` (Extra Small 16×16, Small 32×32, Medium 48×48, Large 96×96) ≈ 36 variants.

**Initials / Medium** (`11:689`):
```
bg #5C00E6 · flex align-items center justify-content center
padding 8px · border-radius 100px · size 48 × 48
initials: Label/Label Large (Manrope Bold 12/14, tracking 4% → 0.48px) · #FFFFFF
```

Nodes: Medium `11:689` · Large `64:4392` · Small `11:685` · XS `50:3170` ·
Pictures Medium `11:675` · Guest Medium `11:683`.

`Avatar / Group` (`11:832`): `Size` (Large `144×48`, Small `104×32`, XS `52×16`) ×
`Labels` False; (Large `213×48`, Small `164×32`, XS `100×16`) × `Labels` True = 6 variants.

---

## 20. Iconography

**Naming convention:** `namespace/icon-name`.

| Namespace | Meaning | Examples |
|---|---|---|
| `interface/` | Standard UI icons | `search` `515:7044`, `info`, `close-circle`, `close-lg`, `warning-circle` |
| `interface/so-*` | "Swing original" — filled/branded style | `so-stars` `1962:92`, `so-love`, `so-checkmark`, `so-tick-circle`, `so-warning-circle`, `so-image`, `so-info` |
| `arrow/` | Directional | `chevron-down` |
| `Logo /` | Brand marks | `Swing Pass icon` `912:14146` (inside component `912:14145`) |

**Observed icon sizes**, by context:

| Size | Context |
|---|---|
| `20 × 20` | Tertiary buttons, page-header back, Tooltip dismiss, Bottom Navigation items, Select chevron |
| `18 × 18` | Tab icons |
| `16 × 16` | Searchbar leading, Text caption, Toaster, Card review star, Select caption |
| `14 × 14` | Button / Actions trailing icon, Toaster action trailing icon |
| `12 × 12` | Tag optional icons, Checkbox checkmark |
| `10 × 10` | Tag Small optional icons |
| `48 × 48` | Card image placeholder |

The Mobile library is authoritative for the icon instances used by its components.
Foundations provides an `Icons (Final)` page (`7:311`) as the source for searching
standalone Swing icons; its complete coverage has not been audited. Use
[icon-logo-usage.md](./icon-logo-usage.md) to inspect, record, export, and implement the
exact asset for a task.

**UNDOCUMENTED:** no universal icon grid, stroke-width specification, or universal
icon-size scale. Sizes above are observed per-context. Do not invent new icons or assume
that a similarly named glyph is the same asset.

---

## 21. Components present in Figma but NOT YET DOCUMENTED

These pages exist in the library but their specs have not been extracted. If a task
touches one, **read the Figma file directly** rather than guessing:

`Button Slider` (`1922:1121`) · `Bar chart` (`115:5020`) · `Chatbox` (`149:4844`) ·
`Chat Bubble` (`1965:1467`) · `Country List` (`723:7345`) ·
`Credit card field` (`32:2522`) · `Datepicker (Calendar)` (`13:313`) ·
`Datepicker (Swivel)` (`632:7058`) · `Divider` (`13:4208`) · `List` (`13:3903`) ·
`Native component` (`26:1859`) · `Pagination` (`28:2448`) ·
`Password field` (`29:2169`) · `PIN Field` (`630:7052`) · `Slider` (`186:7269`) ·
`Star ratings` (`50:3201`) · `Stepper` (`13:5790`) · `Timepicker` (`188:7332`) ·
`Video indicator` (`181:6549`) · `Select field 2` (`2083:86`) ·
`Text field 2` (`2083:2677`) · `Unused / draft` (`13:1999`)

Also present as library components without full specs: `Card / Actions`,
`Card image`, `Golf Course Map`, `Reply card in chat`, `Website card in chat`,
`Date button`, `Modal / Content`, `Text field / Area`, `Text field / Chat`,
`Text field / Comment`.

---

## 22. Full component inventory (`ADS: For Mobile`)

```
Button:        Button / Actions · Button / Tertiary · Button / Destructive ·
               Button Slider · Date button · Checkbox / Button · Radio / Button
Text field:    Text field / Standard · Text field / Area · Text field / Chat ·
               Text field / Comment · Text Field 2 / Standard · Text Field 2 / Area
Card:          Card / Standard · Card / Carousell · Card / Actions ·
               Card / Highlighted scorecard · Card image · Golf Course Card / New ·
               Golf Course Map · Credit card field · Reply card in chat ·
               Website card in chat
Other:         Page header / Standard · Tooltip / Standard · Modal / Content
```
