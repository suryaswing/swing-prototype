---
name: swing-skills-mob
description: "Mandatory design system standard for ALL Swing Mobile UI/UX work. Use when generating a UI design with Figma Make, modifying or improving a design in Figma, writing a Figma Make or Figma Use prompt, using Figma tools or the Figma MCP server, generating or improving Swing Mobile screens, components or user flows, or creating any mobile UI variation, prototype or design exploration. Enforces the official Swing Design System using ADS - Foundations for foundational visual assets and tokens and ADS - For Mobile for mobile component specifications, layout, interaction states, and design quality validation. Read this before touching any Swing design."
argument-hint: 'Describe the Swing Mobile screen, component, or Figma Make prompt you need'
---

# Swing Mobile Design System

**This skill is mandatory, not a reference.** If a task touches Swing Mobile UI/UX in any
way, you read this file and follow the workflow below before producing anything.

**Official design sources:**

- [ADS - Foundations](https://www.figma.com/design/JDN6zpJA4feGSY8ZcQMQeM/ADS--Foundations?node-id=8-12868)
  — `fileKey: JDN6zpJA4feGSY8ZcQMQeM`; foundation palette, elevation, iconography, and
  brand/logo assets.
- [ADS - For Mobile](https://www.figma.com/design/ILlOBW8RpEBRmDvU6LQsx9/ADS--For-Mobile?node-id=149-4844)
  — `fileKey: ILlOBW8RpEBRmDvU6LQsx9`; mobile component specifications, layout, and
  component interaction states.

Use the Foundations file for base visual assets and primitives, then verify how a token
or asset is applied in the Mobile library. Do not treat every foundation color or asset
as an approved mobile component variant.

Never invent a token, measurement, or component specification. New ideas and components
may be proposed within the bounded-innovation rule in §5, but must be labelled as
proposals rather than official Swing standards. If Figma does not define a specification,
mark it **`UNDOCUMENTED`** and follow [§6 Handling missing specifications](#6-handling-missing-specifications).

---

## 1. Project context

| | |
|---|---|
| Platform | Swing Mobile (iOS / Android) |
| Foundation library | `ADS: Foundations` |
| Mobile component library | `ADS: For Mobile` |
| Canonical artboard | **375 × 812** (iPhone 11 Pro / X) |
| Content width | **343px** (375 − 2 × 16) |
| Typeface | **Manrope** only |
| Primary colour | `PURPLE/500 #5C00E6` |
| Minimum touch target | **48 × 48px** |
| Component pages in library | 47 |

Do not substitute the sibling libraries `ADS: For Desktop`, `Minimal_Web`, or
`Eagle - Swing Design System 2.0`. For mobile work, use the two official sources above
with their distinct responsibilities.

> ⚠️ The `index.html` in this repo uses `--ink: #17352b`, `--green: #2d654d` and DM Sans.
> **Those are prototype-only and are NOT Swing tokens.** Never cite or copy them.

---

## 2. Mandatory workflow

Follow all five steps, in order, for **every** design-related request.

### Step 1 — Read the skill

Read this file, then load only the reference files relevant to the task
(see [§4 References](#4-reference-files)). Do not rely on remembered design values.

If the request includes a PRD, product brief, or requirements document, first follow
[`swing-prd-review`](../swing-prd-review/SKILL.md) to check product behavior, edge cases,
and design-blocking questions. Carry confirmed requirements and any explicitly accepted
assumptions into the design. Do not treat unresolved PRD questions as approved product
behavior. If no PRD is available, clarify material product-flow ambiguity or mark it as
an assumption before designing.

### Step 2 — Inspect the official Figma design system

Use the Figma MCP server to inspect both official sources: `JDN6zpJA4feGSY8ZcQMQeM`
for foundation colors, elevation, icons and logos, and `ILlOBW8RpEBRmDvU6LQsx9` for
mobile components, layout and interaction states. **Do not rely solely on previously
remembered design information** — re-verify what the task depends on.

For an icon/logo request, inspect the exact asset in Foundations first, then confirm
its intended mobile usage in the relevant Mobile component. For a color or elevation,
inspect the foundation token and the Mobile component that applies it; if no mobile
usage is established, disclose that rather than implying it is a standard component
variant.

Practical MCP notes:

- `get_metadata` with **no** `nodeId` lists the pages of the queried file — the cheapest
  way to orient. The Mobile library has 47 pages.
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
components, tokens, patterns, icons, logos and states should be reused. For icon/logo
selection and asset handling, follow
[icon-logo-usage.md](./references/icon-logo-usage.md); inspect the exact Figma asset and
record its verified name and node ID.

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

COMPONENTS — reuse these existing Swing components wherever they fit:
- <component name> (<variant props>) — <usage>

ICONS & LOGOS:
- <Figma asset name> (<node ID>, <size/variant>) — <role and local asset path if exported>
- Use exact Swing assets; do not replace them with emoji, text glyphs, or improvised marks.

NEW IDEAS / COMPONENTS:
- Keep genuinely new component and interaction-pattern roles to about 30% or less of the screen.
- Explain why each cannot be covered by an existing Swing component or established pattern.
- Build proposals with verified Swing tokens; label them as proposals, not official standards.

REQUIRED STATES:
- <e.g. field Default / Focused / Error / Disabled; button Default / On press / Loading / Disabled>

LAYOUT:
- <structure, in order, with the spacing tokens above>

DO NOT:
- Invent colours, type styles, radii or shadows.
- Use any font other than Manrope.
- Deviate from 343px content width.
- Exceed the ~30% new component / pattern allowance without disclosing it and getting approval.
```

Fill every `<...>` with real values from the reference files. If a value is not in the
reference files, go to Figma — and if it is not in Figma either, mark it `UNDOCUMENTED`
rather than filling the gap.

---

## 4. Reference files

Load only what the task needs.

| File | Read when |
|---|---|
| [references/design-foundations.md](./references/design-foundations.md) | Source responsibilities, foundation page map, and verified examples |
| [references/design-tokens.md](./references/design-tokens.md) | **Start here.** Cross-file index + quick-reference token tables |
| [references/color-system.md](./references/color-system.md) | Choosing any colour, fill, border, or semantic state |
| [references/typography.md](./references/typography.md) | Choosing any type style, size, weight or tracking |
| [references/spacing-layout.md](./references/spacing-layout.md) | Laying out a screen: padding, gaps, heights, radius, elevation, touch targets |
| [references/components.md](./references/components.md) | Selecting or specifying any component (22 sections + full inventory) |
| [references/icon-logo-usage.md](./references/icon-logo-usage.md) | Selecting, documenting, exporting, or implementing icons and logos |
| [references/icon-logo-usage.md](./references/icon-logo-usage.md) | Selecting, documenting, exporting, or implementing icons and logos |
| [references/interaction-patterns.md](./references/interaction-patterns.md) | States, feedback, navigation behaviour, overlays |
| [references/design-quality-checklist.md](./references/design-quality-checklist.md) | **Before presenting.** Validation + mandatory disclosure block |

---

## 5. Component reusability rules

1. **Reuse an existing Swing component whenever it fulfils the need.** A new idea or
   component is allowed when no existing component or established Swing pattern fits.
2. **Respect existing component properties and variants** — do not flatten or extend them
   ad hoc.
3. **Maintain consistent behaviour and interaction states** across every instance.
4. **Allow bounded innovation:** keep genuinely new component and interaction-pattern
   roles to about 30% or less of the screen; aim for at least 70% reuse of existing
   Swing components or established Swing patterns.
5. Count distinct component/pattern roles, not repeated instances. Calculate
   `new roles ÷ all roles × 100`; exclude primitive text, spacing, and decoration from
   the count. State the count and approximate percentage in the handoff.
6. If the screen has fewer than four roles, disclose the resulting ratio; do not silently
   exceed the allowance. Ask before exceeding it unless the user has already approved
   the specific exception.
7. For every new role, **explain why reuse was not possible** and name the closest
   existing component or pattern considered.
8. Use verified Swing tokens and document interaction behavior. Mark unsupported
   product behavior or visual specifications `UNDOCUMENTED`; do not present proposals
   as official Swing standards.
9. Recommend genuinely useful new components for standardisation in future Swing work.

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

**Consistency is mandatory. Creativity may introduce new ideas within the ~30% allowance,
while reusing Swing patterns and staying within verified design tokens.**

---

## 9. Keeping this skill in sync with Figma

The Figma library remains the source of truth; these Markdown references are a maintained
snapshot and do not update automatically. When the user says a component or token changed:

1. Ask for or use the relevant Figma file/page/component link. Confirm it is in
   `ADS: Foundations` or `ADS: For Mobile`, and determine which file owns the changed
   specification; do not infer a change from a screenshot or description alone when
   exact specifications matter.
2. Inspect the current component in Figma MCP. Record its page, component/variant name,
   node ID, properties, states, geometry, and styles that are relevant to the change.
3. Compare the live Figma data with the existing reference. Report material differences,
   including removed or renamed variants. Do not silently normalize inconsistencies.
4. Update only the affected sections in `references/design-foundations.md`,
   `references/components.md`, `references/icon-logo-usage.md`, and the relevant token references
   (`color-system.md`, `typography.md`, `spacing-layout.md`, `interaction-patterns.md`,
   or `design-tokens.md`). Update the quality checklist's known-gap list if the change
   resolves or introduces a documented gap.
5. Cite Figma node IDs and distinguish verified updates from details still missing or
   unverified. Do not infer undocumented states or measurements.
6. Keep the `.claude/skills/swing-skills-mob/` tree as the single repository copy; do not
   recreate a `.github/skills/` mirror unless the user explicitly requests it.
7. Summarize what changed and what could not be verified. Do not commit or push unless
   the user asks.

For routine design tasks, inspect the relevant live component before use as described in
§2, but do not rewrite the skill references unless the user requests a documentation
refresh or a clear material mismatch is discovered. In the latter case, flag the stale
reference and ask whether to update the skill when changing documentation is outside the
requested task.
