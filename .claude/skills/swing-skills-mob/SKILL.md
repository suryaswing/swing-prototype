---
name: swing-skills-mob
description: "Mandatory design system standard for ALL Swing Mobile UI/UX work. Use when generating a UI design with Figma Make, modifying or improving a design in Figma, writing a Figma Make or Figma Use prompt, using Figma tools or the Figma MCP server, generating or improving Swing Mobile screens, components or user flows, or creating any mobile UI variation, prototype or design exploration. Enforces the official Swing Mobile Design System from the ADS - For Mobile Figma file: colour palette, Manrope typography scale, spacing and 375px layout, component reuse rules, interaction states, and design quality validation. Read this before touching any Swing design."
argument-hint: 'Describe the Swing Mobile screen, component, or Figma Make prompt you need'
---

# Swing Mobile Design System

**This skill is mandatory, not a reference.** If a task touches Swing Mobile UI/UX in any
way, you read this file and follow the workflow below before producing anything.

**Source of truth:**
[ADS - For Mobile](https://www.figma.com/design/ILlOBW8RpEBRmDvU6LQsx9/ADS--For-Mobile?node-id=149-4844)
— `fileKey: ILlOBW8RpEBRmDvU6LQsx9`

Never invent a token, measurement, or component. If Figma does not define it, mark it
**`UNDOCUMENTED`** and follow [§5 Missing specifications](#5-handling-missing-specifications).

---

## 1. Project context

| | |
|---|---|
| Platform | Swing Mobile (iOS / Android) |
| Figma library | `ADS: For Mobile` |
| Canonical artboard | **375 × 812** (iPhone 11 Pro / X) |
| Content width | **343px** (375 − 2 × 16) |
| Typeface | **Manrope** only |
| Primary colour | `PURPLE/500 #5C00E6` |
| Minimum touch target | **48 × 48px** |
| Component pages in library | 47 |

Do **not** confuse this with the sibling Figma libraries `ADS: For Desktop`,
`ADS: Foundations`, `Minimal_Web`, or `Eagle - Swing Design System 2.0`. Only
`ADS: For Mobile` governs mobile work.

> ⚠️ The `index.html` in this repo uses `--ink: #17352b`, `--green: #2d654d` and DM Sans.
> **Those are prototype-only and are NOT Swing tokens.** Never cite or copy them.

---

## 2. Mandatory workflow

Follow all five steps, in order, for **every** design-related request.

### Step 1 — Read the skill

Read this file, then load only the reference files relevant to the task
(see [§4 References](#4-reference-files)). Do not rely on remembered design values.

### Step 2 — Inspect the official Figma design system

Use the Figma MCP server against `ILlOBW8RpEBRmDvU6LQsx9` to inspect the relevant
pages, frames, components, styles and variables. **Do not rely solely on previously
remembered design information** — re-verify what the task depends on.

Practical MCP notes:

- `get_metadata` with **no** `nodeId` lists all 47 pages — the cheapest way to orient.
- `get_metadata` on a page returns its child frame/symbol IDs.
- `get_design_context` works on `<frame>` and `<symbol>` nodes, **not** on `<canvas>`
  (page) nodes. If it fails, get a child frame ID from `get_metadata` first.
- `get_design_context` on a `<text>` node returns only that node — call `get_metadata`
  on it to drill into the group.
- Never guess a sibling node ID by pattern; a deleted ID returns "not found".
- Every `get_design_context` response ends with **"These styles are contained in the
  design:"** — this is the primary token-extraction channel.
- `get_variable_defs` requires a live selection in the Figma app and will fail
  headlessly. Do not depend on it.

### Step 3 — Identify applicable components

Search [components.md](./references/components.md) §22 (full inventory) and §21
(not-yet-documented pages) **before** drawing anything. Determine which existing Swing
components, tokens, patterns and states should be reused.

**Prioritise existing components over creating new ones.**

### Step 4 — Apply Swing design standards

Every prompt, screen and modification must follow the documented system. See
[§3 Prompt generation](#3-figma-make--figma-use-prompt-rules) and
[components.md](./references/components.md).

### Step 5 — Validate the result

Run the full procedure in
[design-quality-checklist.md](./references/design-quality-checklist.md), including the
mandatory compliance disclosure block. Identify inconsistencies, missing specifications
and deviations — and state which requirement could not be validated.

---

## 3. Figma Make / Figma Use prompt rules

When you generate a prompt for Figma Make or Figma Use, **embed the actual Swing
specifications into the prompt**. A prompt that merely says "follow the design system"
is a failed prompt — the model cannot see the design system.

Every generated prompt must communicate:

1. Follow the official Swing Mobile Design System.
2. Reuse existing Swing components wherever possible.
3. Use the correct design tokens and typography.
4. Maintain consistent spacing and layout.
5. Follow established interaction patterns.
6. Maintain visual consistency with existing Swing screens.
7. Do not introduce arbitrary colours, typography, components or visual styles.
8. The result must feel like a native part of the existing Swing application.

And it must be **specific and actionable**, with the real values inline.

### Prompt template

```
Design a <screen/component> for Swing Mobile.

DESIGN SYSTEM (mandatory — do not deviate):
- Artboard: 375 × 812. Content width 343px. Horizontal padding 16px.
- Typeface: Manrope only.
  · Screen title: Manrope ExtraBold 800, 18px / 22px, letter-spacing -0.36px (Heading/H5)
  · Section head: Manrope ExtraBold 800, 14px / 18px, letter-spacing -0.28px (Heading/H6)
  · Body:         Manrope Regular 400, 14px / 22px, letter-spacing 0.28px (Body/B1)
  · Secondary:    Manrope Regular 400, 12px / 20px, letter-spacing 0.24px (Body/B2)
  · Caption:      Manrope Bold 700, 10px / 16px, letter-spacing 0.20px (Body/B3 Semibold)
  · Button label: Manrope Bold 700, 16px / 20px, letter-spacing 0.32px (CTA/Button Large)
- Colours (use exactly these):
  · Primary action      PURPLE/500  #5C00E6
  · Primary pressed     PURPLE/600  #4900B8
  · Surface             LIGHT/100   #FFFFFF
  · Field fill          LIGHT/300   #F2F2F5
  · Divider             LIGHT/500   #E4E4EB
  · Primary text        DARK/500    #1C1C28
  · Secondary text      DARK/300    #555770
  · Placeholder / meta  DARK/200    #8F90A6
  · Border / inactive   DARK/100    #C7C9D9
  · Error               RED/500     #FF2A12   (field fill RED/50 #FFF8F5)
  · Success             GREEN/500   #36B37E   (field fill GREEN/50 #EFFFF7)
  · Warning             ORANGE/500  #FF8113   (field fill ORANGE/50 #FFF9EE)
- Radius: 4px cards/checkbox · 8px buttons & inputs & modals · 12px large searchbar · 100px pills
- Elevation: Elevation Small 0 2px 8px rgba(0,0,0,0.08) · Elevation Large 0 16px 24px rgba(0,0,0,0.22)
- Touch targets: minimum 48 × 48px.

COMPONENTS — reuse these existing Swing components, do not redraw them:
- <component name> (<variant props>) — <usage>

REQUIRED STATES:
- <e.g. field Default / Focused / Error / Disabled; button Default / On press / Loading / Disabled>

LAYOUT:
- <structure, in order, with the spacing tokens above>

DO NOT:
- Invent colours, type styles, radii, shadows or components.
- Use any font other than Manrope.
- Deviate from 343px content width.
```

Fill every `<...>` with real values from the reference files. If a value is not in the
reference files, go to Figma — and if it is not in Figma either, mark it `UNDOCUMENTED`
rather than filling the gap.

---

## 4. Reference files

Load only what the task needs.

| File | Read when |
|---|---|
| [references/design-tokens.md](./references/design-tokens.md) | **Start here.** Cross-file index + quick-reference token tables |
| [references/color-system.md](./references/color-system.md) | Choosing any colour, fill, border, or semantic state |
| [references/typography.md](./references/typography.md) | Choosing any type style, size, weight or tracking |
| [references/spacing-layout.md](./references/spacing-layout.md) | Laying out a screen: padding, gaps, heights, radius, elevation, touch targets |
| [references/components.md](./references/components.md) | Selecting or specifying any component (22 sections + full inventory) |
| [references/interaction-patterns.md](./references/interaction-patterns.md) | States, feedback, navigation behaviour, overlays |
| [references/design-quality-checklist.md](./references/design-quality-checklist.md) | **Before presenting.** Validation + mandatory disclosure block |

---

## 5. Component reusability rules

1. **Never create a new component when an existing Swing component fulfils the need.**
2. **Respect existing component properties and variants** — do not flatten or extend them
   ad hoc.
3. **Maintain consistent behaviour and interaction states** across every instance.
4. **Avoid unnecessary visual deviations.**
5. If a new component is genuinely required, **explain why the existing component cannot
   be reused** — and name the closest existing component you rejected.
6. **Recommend new components that can be standardised** for future Swing features.

Component search order:

```
components.md §22  (ADS: For Mobile inventory)
  → components.md §1–20  (fully documented components)
    → components.md §21  (pages not yet documented → go to Figma)
      → Figma MCP on ILlOBW8RpEBRmDvU6LQsx9
```

---

## 6. Handling missing specifications

When Figma does not contain a specification:

1. **Do not invent an official Swing standard.**
2. Look for a similar existing pattern elsewhere in the Swing Figma file.
3. Use the closest established pattern if appropriate.
4. **Clearly distinguish** existing standards from AI recommendations.
5. **Ask for clarification** if the missing specification materially affects the design.

Disclose in this format:

```
⚠️ UNDOCUMENTED: <what is missing>
Found instead:   <closest existing pattern + node ID, or "none">
Suggested:       <recommendation, labelled as a recommendation>
Needs decision:  <specific question>
```

Known gaps are catalogued in
[design-quality-checklist.md §5](./references/design-quality-checklist.md) — check that
list before assuming something is missing.

---

## 7. Design quality requirements

Before completing **any** design task, validate:

- Does the design follow Swing's official colour palette?
- Is typography consistent with Swing standards?
- Are spacing and margins consistent?
- Are existing components reused appropriately?
- Are button and input states consistent?
- Are interaction patterns aligned with the existing application?
- Is the information hierarchy clear?
- Is the design responsive to mobile screen dimensions?
- Are empty, loading, error and success states considered where relevant?
- Does the final design visually belong to the Swing ecosystem?

**If any requirement cannot be validated, disclose it.**

Full procedure and the mandatory compliance block:
[design-quality-checklist.md](./references/design-quality-checklist.md).

---

## 8. Non-negotiables

| # | Rule |
|---|---|
| 1 | This skill is read before any Swing Mobile design work — no exceptions |
| 2 | Figma is inspected live; remembered values are not trusted |
| 3 | No invented tokens, measurements or component specs |
| 4 | Every gap is marked `UNDOCUMENTED`, never silently filled |
| 5 | Existing components are reused before new ones are drawn |
| 6 | Every deliverable ends with the compliance disclosure block |
| 7 | Manrope only — no other typeface |
| 8 | 375 × 812 artboard, 343px content width, 48 × 48px touch targets |
| 9 | Inconsistencies found in Figma are documented as-is, never normalised away |
| 10 | The result must read as a native part of the Swing application |

**Consistency is mandatory. Creativity operates within Swing's established design
standards.**
