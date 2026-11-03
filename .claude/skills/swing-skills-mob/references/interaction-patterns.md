# Swing Mobile — Interaction Patterns

State systems, feedback patterns and behavioural rules extracted from **ADS: For Mobile**
(`ILlOBW8RpEBRmDvU6LQsx9`).

---

## 1. The state vocabulary

Swing components use a small, repeated set of state names. Learn these — they recur
across every component.

| State name | Meaning |
|---|---|
| `Default` | Resting, untouched |
| `Focused` | Keyboard/scroll focus; also used for the selected nav/tab item |
| `On press` | Active/pressed moment |
| `Typing` | Input has focus and content is being entered |
| `Completed` | Input has valid content and lost focus |
| `Disabled` | Non-interactive |
| `Selected` | Chosen (checkbox, radio, select value) |
| `Indeterminate` | Checkbox tri-state |
| `Warning` | Error state on Text field (see naming trap below) |
| `Success` | Validated state |

> ⚠️ **Naming trap:** the Text field matrix calls the error state **`Warning`**, but node
> `13:2999` renders red (`#FF2A12`), not orange. Treat field "Warning" as **error**.
> `Panel` / `Focus status` / `Type` etc. vary per component — always read the actual
> variant matrix rather than assuming a prop set.

---

## 2. Input field lifecycle

The documented flow for a text field:

```
Default  →  Focused  →  Typing  →  Completed
   ↓                      ↓
Disabled            Warning (error) / Success
```

| Transition | Visual change |
|---|---|
| Default → Focused | Add `border 1px solid #5C00E6`; background stays `#F2F2F5` |
| Typing | Same as Focused; content colour `#1C1C28` |
| Completed | Border removed; value `#1C1C28` |
| → Warning/Error | Background `#FFF8F5`, border `1px solid #FF2A12`, placeholder `#FF2A12`, caption with `interface/so-warning-circle` |
| → Success | Background `#EFFFF7`, border `1px solid #36B37E`, value `#1C1C28`, caption with `interface/so-tick-circle` |
| → Disabled | Background `#F2F2F5`, no border, value `#8F90A6` |

**Height reservation:** the Error and Success states are `110px` tall **even when
`Text caption = False`** — the caption space is reserved so the layout does not jump
when validation fires. Reproduce this; do not let the field grow on error.

---

## 3. Selection controls

| Control | Off / Unselected | On / Selected | Pressed |
|---|---|---|---|
| **Toggle** | track `#C7C9D9`, indicator left | track `#5C00E6`, indicator right | — (State = Default/Disabled only) |
| **Checkbox** | `bg #FFFFFF`, `border 1px #C7C9D9`, radius `4px` | `bg #5C00E6`, `border 1px #5C00E6`, 12×12 checkmark | `On press` state |
| **Radio** | `bg #FFFFFF`, `border 1px #C7C9D9`, radius `100px` | fill `#4900B8` | `On press` state |
| **Tab** | label `#1C1C28`, indicator `bg #FFFFFF` h2px | label `#5C00E6`, indicator `bg #5C00E6` h2px | — |
| **Bottom nav item** | icon + label `#1C1C28` | `Focused` state | — |

> **Verified inconsistency:** Radio uses `PURPLE/600 #4900B8` while Checkbox and Toggle
> use `PURPLE/500 #5C00E6`. This is real — reproduce it.

**Tap targets:** Radio/Button, Checkbox/Button and Toggle are all **48 × 48**. The
labelled variants (`Radio / Label` 91×20, `Checkbox / Label` 116×20) keep the 20px
control with an `8px` gap to the label.

---

## 4. Feedback & notification patterns

### Toaster — transient message

Five documented types. Use the type that matches the semantic, not an arbitrary colour.

| Type | Background | When to use |
|---|---|---|
| **Success** | `#36B37E` | Action completed |
| **Error** | `#FF2A12` | Action failed, destructive result |
| **Warning** | `#FF8113` | Non-blocking caution |
| **Neutral** | `#8F90A6` | Informational |
| **Other actions** | `#5C00E6` | Message that needs a follow-up action |

Structure: `375 × 64`, icon `16×16` + message `Body/B3 Semibold` white, optional trailing
action (`Button / Tertiary`, label `CTA/Button Small` white, trailing icon `14×14`,
e.g. "See my cart"). Shadow `Elevation Large`.

### Loader — blocking progress

`224 × 224` white card, `Elevation Large`, `radius 8px`, `padding 32px`.
`96 × 96` spinner + optional label block (`Body/B1` line 1, `Body/B1 Semibold` line 2).
Four variants from `Label` × `Percentage`. Use `Percentage=True` when progress is
determinate.

### Text caption — inline field feedback

`16px` tall, icon `16 × 16` + `Body/B3 Semibold`, gap `8px`. Four types: Error
(`#FF2A12`), Warning (**unverified hex**), Success (`#36B37E`), Neutral (`#8F90A6`).
Sits directly under the input as part of the field's `flex column gap 4px` stack.

### Tooltip — contextual helper

Dark `#28293D` card, `padding 14px`, `radius 8px`, label `Body/B1 Semibold` white,
`Elevation Large`, `48 × 8` pointer. Four positions. Optional trailing dismiss button.

---

## 5. Navigation behaviour

### Bottom Navigation

`375 × 86`, 3 or 4 items, each `75px` wide with `20 × 20` icon + `Body/B3 Semibold` label
(`gap 4px`). Items carry `State` (Default, Focused) and an optional `Notification badge`.
Item types documented: Home, Feed, Activities, Chats, Friends, Account, Feed post,
Default. **Focused is the selected state** — no separate "selected" prop.

### Tab

Two families:
- **Fixed width** (`13:9265`) — 2, 3 or 4 tabs, total `375 × 36`.
- **Flexible width** (`13:9266`) — 2–7 tabs; widths 132 / 199 / 266 / 333 / 400 / 466px.
  Beyond 5 tabs the set exceeds the 375px frame, implying horizontal scroll rather than
  compression.

Tab item: `px 16px py 8px`, optional `18 × 18` icon with `8px` gap, label `Heading/H6`,
`2px` indicator with `4px` top radius. Focused = `#5C00E6` label + indicator.

### Page header

`375 × 48` standard. Six families exist for different screens — `Standard`, `Home`,
`Home Public`, `Activities`, `Chats`, `Explore`. Choose the family by screen type; do not
build a bespoke header. Back navigation uses `Button / Tertiary` with a `20 × 20` icon.

---

## 6. Overlay patterns

### Modal / bottom sheet

`Sheet Grabber` (`28:2154`): white container, `pt 8px`, `px 163px`, `radius 8px 8px 0 0`,
`375px` wide, containing a `48 × 4` `#E4E4EB` bar at `radius 100px`.

The grabber is the visual affordance for a draggable sheet — include it on any
bottom-sheet-style surface.

Modal variants cover: header (`Title + description` / `Title only` / `Description only`,
with or without `Actions`), content with keyboard, dialog with/without image, list modal,
share modal (5 states), and header actions (searchbar / tags / both).

---

## 7. Interaction rules for AI agents

1. **Every interactive element needs its documented states.** If you generate a button
   without `On press` / `Disabled`, it is incomplete.
2. **Use the documented state names** when describing a design — `Focused`, not
   "active" or "highlighted".
3. **Minimum 48 × 48 tap target** for icon and control targets. This is the observed
   standard across Radio, Checkbox, Toggle and Tertiary button.
4. **Reserve space for error captions** — do not shift layout on validation.
5. **Pick the toaster type semantically**, not by colour preference.
6. **Do not invent animation specs.** See §8.

---

## 8. Motion & animation — UNDOCUMENTED

The Figma library contains **no** motion specification: no duration tokens, no easing
curves, no transition definitions, no prototype interactions captured as specs.

If a task asks for animation:

- Design it as a **recommendation**, explicitly labelled as such.
- Use only `transform` and `opacity` (compositor-friendly).
- Keep durations subtle (~150–300ms) and always respect `prefers-reduced-motion`.
- Never present a duration or easing as a "Swing standard".

> The `index.html` prototype's `drift` / `rise` / `fade` / `shake` keyframes are
> **prototype-only** and are not part of the Swing design system.

---

## 9. Undocumented interaction areas

| Area | Status |
|---|---|
| Gestures (swipe, long-press, pull-to-refresh) | **UNDOCUMENTED** |
| Haptic feedback | **UNDOCUMENTED** |
| Transition / animation timings | **UNDOCUMENTED** |
| Focus order & keyboard navigation | **UNDOCUMENTED** |
| Screen-reader labels / ARIA | **UNDOCUMENTED** |
| Error message copy guidelines | **UNDOCUMENTED** |
| Empty-state patterns | **UNDOCUMENTED** (no empty-state component in the library) |
| Offline / network-loss behaviour | **UNDOCUMENTED** |
| Safe area / notch insets | **UNDOCUMENTED** |
| Toast duration / stacking rules | **UNDOCUMENTED** |
| Loading skeleton patterns | **UNDOCUMENTED** (only the Loader card exists) |
