# Swing Mobile — Design Quality Checklist

Run this **before** presenting any Swing Mobile design deliverable. Anything you cannot
verify must be disclosed — never silently assumed.

---

## 1. Required validation (user-specified, verbatim)

Before completing any design-related task, validate:

- [ ] Does the design follow **Swing's official colour palette**?
  → every fill/stroke/text colour traces to a token in [color-system.md](./color-system.md);
    check mobile usage against [design-foundations.md](./design-foundations.md)
- [ ] Is **typography** consistent with Swing standards?
  → every text node uses a named style from [typography.md](./typography.md); Manrope only
- [ ] Are **spacing and margins** consistent?
  → values come from [spacing-layout.md](./spacing-layout.md); no invented gaps
- [ ] Are **existing components reused** appropriately?
  → matched against [components.md](./components.md) before anything new is drawn
- [ ] Are **icons and logos** exact Swing assets, named and source-linked?
  → matched against [icon-logo-usage.md](./icon-logo-usage.md); no text or emoji logo substitutes
- [ ] Are **button and input states** consistent?
  → Default / On press / Disabled at minimum; fields show Focused / Error / Success
- [ ] Are **interaction patterns** aligned with the existing application?
  → per [interaction-patterns.md](./interaction-patterns.md)
- [ ] Is the **information hierarchy** clear?
  → H5/H6 for headings, B1/B2 for body, B3 for captions; one H5 per surface
- [ ] Is the design **responsive to mobile screen dimensions**?
  → designed at 375 × 812, 343px content width
- [ ] Are **empty, loading, error and success states** considered where relevant?
- [ ] Does the final design **visually belong to the Swing ecosystem**?

**If any requirement cannot be validated, disclose it.**

---

## 2. Token compliance sweep

Before presenting, grep the deliverable for anything that is not a token.

| Check | Fail condition |
|---|---|
| Hex colours | Any hex not in the palette table |
| Non-Manrope font | Any `font-family` other than Manrope |
| Arbitrary font size | Any `font-size` not in the type scale |
| Arbitrary tracking | Any `letter-spacing` not derived from the percent formula |
| Arbitrary radius | Any radius other than `4 / 8 / 12 / 100px` |
| Arbitrary shadow | Any shadow other than `Elevation Small` / `Elevation Large` |
| Arbitrary spacing | Any padding/gap not in the observed value set |
| New component / pattern | More than about 30% of distinct component and interaction-pattern roles are novel, or a new role duplicates an existing component |

> ⚠️ **`index.html` warning:** the prototype in this repo uses `--ink: #17352b`,
> `--green: #2d654d`, `--line: #dce5df`, `--paper: #fbfcfa` and DM Sans. **These are
> prototype-only and are NOT Swing design tokens.** Never copy them into a Swing
> deliverable or cite them as a source.

---

## 3. Component reuse audit

For every component in the deliverable:

1. Did I search `components.md` §22 (full inventory) and §21 (undocumented pages) first?
2. Does an existing Swing component satisfy the requirement?
   - **Yes** → use it, and state its Figma name (e.g. `Button / Actions`).
   - **No** → justify in writing why the closest existing component cannot be reused.
3. Does my instance respect the component's documented props and variants?
4. Do all interactive states exist?

New components and interaction patterns are allowed when existing Swing components or
established patterns do not fit. Keep them to **about 30% or less of distinct roles** in
the design, aiming for at least 70% reuse. Count roles, not repeated instances; exclude
primitive text, spacing, and decoration. Report `new roles / all roles` and the resulting
approximate percentage. If fewer than four roles make the ratio exceed the allowance,
disclose it and ask before proceeding unless that specific exception was already approved.

For each new role, explain why reuse is not possible and name the closest existing
component or pattern considered. Use verified Swing tokens; label the design as a
proposal, not an official standard. Recommend genuinely reusable additions for
standardisation.

---

## 4. Undocumented-spec handling procedure

Follow this order exactly. Never skip to step 5.

1. **Do not invent an official Swing standard.**
2. Search the Swing Figma file for a similar existing pattern
   (start at [components.md](./components.md) §21–22 and go to Figma if needed).
3. If a close pattern exists, use it — and label it as *the closest established pattern*.
4. **Clearly distinguish** existing standards from AI recommendations in the output.
5. **Ask for clarification** if the missing specification materially affects the design.

### Disclose the gap in this format

```
⚠️ UNDOCUMENTED: <what is missing>
Found instead:   <closest existing pattern + node ID, or "none">
Suggested:       <recommendation, labelled as a recommendation>
Needs decision:  <the specific question to resolve>
```

---

## 5. Known gaps — check this list first

These are confirmed missing from the Figma library. If a task touches one, disclose
immediately rather than filling the hole with a guess.

| Area | Status |
|---|---|
| Global grid / column / gutter system | **UNDOCUMENTED** — `Page grid` holds only a 375×812 frame |
| Responsive / tablet / breakpoint rules | **UNDOCUMENTED** |
| Semantic token aliases (`color.action.primary` style names) | **UNDOCUMENTED** |
| Dark mode / theming / variable modes | **UNDOCUMENTED** |
| Motion: durations, easing, transitions | **UNDOCUMENTED** |
| Gestures (swipe, long-press, pull-to-refresh) | **UNDOCUMENTED** |
| Haptics | **UNDOCUMENTED** |
| Accessibility: contrast rules, focus order, screen-reader labels, ARIA | **UNDOCUMENTED** |
| Minimum body font-size rule | **UNDOCUMENTED** (scale reaches 8px) |
| Universal icon grid, stroke width, completeness of `Icons (Final)` catalog, logo clear-space rules and full logo lockup inventory | **UNDOCUMENTED** — Foundations has icon and logo pages, but coverage and universal rules have not been verified |
| Empty-state component / pattern | **UNDOCUMENTED** |
| Error-message copy guidelines | **UNDOCUMENTED** |
| Toast duration, stacking, dismissal rules | **UNDOCUMENTED** |
| Safe-area / notch insets | **UNDOCUMENTED** |
| Font fallback stack & loading strategy | **UNDOCUMENTED** |
| Full-page screen templates or user flows | **NOT PRESENT** — the file is a component library |
| Warning text-caption hex (`11:1469`) | **UNVERIFIED** — `#FF8113` is an inference |
| `Select field 2`, `Text field 2` generations | **NOT YET DOCUMENTED** |
| Modal interiors, List, Divider, Slider, Stepper, Pagination, Star ratings, Bar chart, Datepicker, Timepicker, Chatbox, Chat Bubble, Password field, PIN field, Credit card field, Country List, Native component, Video indicator, Button Slider | **NOT YET DOCUMENTED** — read Figma directly |

---

## 6. Deliverable disclosure block

End every design deliverable with this block. It is not optional.

```markdown
## Swing Design System Compliance

**Components reused:**
- <Figma component name> (<node ID>) — <where used>

**New components proposed:**
- <name> — <why reuse was not possible> — <count/ratio, e.g. 2 of 8 roles = 25%>
  OR: None — all requirements covered by existing components.

**New component / pattern allowance:**
- <new roles / total roles = approximate percentage, and how the count was made>

**Icons and logos:**
- <asset name> (<Figma node ID>) — <role, verified variant/size, and local file if exported>

**Tokens applied:**
- Colours: <list or "all from color-system.md">
- Type styles: <list>
- Radius / elevation: <list>

**Deviations from the design system:**
- <deviation> — <reason> — <needs approval?>
  OR: None.

**Undocumented specifications encountered:**
- <item> — <how handled> — <needs decision?>

**Not validated:**
- <item> — <why it could not be verified>
  OR: None.
```

---

## 7. Pre-flight summary

A deliverable is ready only when all of these are true:

| # | Gate |
|---|---|
| 1 | `SKILL.md` was read and the 5-step workflow was followed |
| 2 | The Figma file was inspected live this session (not recalled from memory) |
| 3 | Every colour, size, radius and shadow is a verified token |
| 4 | Every component maps to a named Figma component, or is justified as new |
| 5 | All required interaction states are present |
| 6 | Layout is at 375px with 343px content width (or the deviation is disclosed) |
| 7 | Empty / loading / error / success states are handled or explicitly deferred |
| 8 | Every gap from §5 that the task touches is disclosed |
| 9 | The compliance block from §6 is included |
| 10 | The result visually reads as a native part of the Swing application |

Failing any gate = the deliverable is not ready. Fix it or disclose it.
