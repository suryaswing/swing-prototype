---
description: Create, edit, extend, and review Swing Sports interfaces in
  Figma Design and Figma Make. Use this skill whenever a task involves
  Swing, Swing Golf, Swing mobile or web UI, prototypes, components,
  design-system compliance, or visual updates to an existing Swing
  product. Always establish the current Swing design-system source of
  truth before designing.
name: swing-skills-figma
---

# Swing Figma Design Skill

## Purpose

You are designing for **Swing Sports**. Your work must follow Swing's
actual product design language, existing design system, interaction
patterns, and component conventions.

This skill applies to: - Creating new Swing screens, flows, and product
experiences. - Generating or editing interfaces in Figma Design or Figma
Make. - Updating existing Swing components, layouts, prototypes, or
responsive behavior. - Reviewing or improving an existing Swing
interface. - Translating a product requirement, wireframe, or reference
into Swing UI.

Do not produce generic template UI when the task is for Swing.

## Source of truth --- mandatory

Before creating or changing any Swing UI, consult these sources in this
order:

1.  **Swing Mobile skill repository**\
    https://github.com/suryaswing/swing-prototype/tree/main/.claude/skills/swing-skills-mob

2.  **Swing Mobile Design System in Figma**\
    https://www.figma.com/design/ILlOBW8RpEBRmDvU6LQsx9

3.  **The active Figma file and its available libraries, variables,
    styles, and components.**

The repository contains the detailed Swing skill and supporting
design-system documentation. The Figma file is the visual and structural
reference. The active library is the implementation source for
components and tokens.

### Mandatory reading and verification procedure

Before design work:

1.  Check whether the repository and its design-system references are
    available in the current context.
2.  Read the relevant Swing Mobile skill instructions and supporting
    documentation where accessible. Prioritize:
    -   `design-tokens.md`
    -   `color-system.md`
    -   `typography.md`
    -   `spacing-layout.md`
    -   `components.md`
    -   `interaction-patterns.md`
    -   `design-quality-checklist.md`
3.  Inspect the Swing Design System Figma file when access is available.
    Verify actual component names, variants, variables, styles,
    dimensions, and behavior rather than relying on memory.
4.  Inspect the target file to understand its page structure, existing
    patterns, local components, and current implementation.
5.  Apply the most relevant rules to the requested task.

**Do not claim that you have read a file, inspected a component, or
verified a token unless you actually accessed it.**

If a linked source cannot be accessed: - State exactly which source is
unavailable. - Use only the Swing rules that are explicitly available in
this skill and in the current Figma file. - Ask the user to provide the
missing reference or grant access when it is necessary for accuracy. -
Do not invent missing token names, component specifications, or design
rules.

If sources conflict, prefer the current approved Swing Figma Design
System and active library. Flag meaningful conflicts instead of silently
inventing a resolution.

## Swing visual foundations

The following values are known Swing brand colors. Treat them as
brand-level reference values, not as permission to use them arbitrarily
in every component or state.

  Color role / reference   Value
  ------------------------ -----------
  Purple                   `#5C00E6`
  Pink                     `#FF00DD`
  Teal                     `#00B0E6`
  Orange                   `#FF8113`
  Green                    `#36B37E`
  Red                      `#FF2A12`

Swing also maintains DARK and LIGHT neutral ramps. Retrieve the exact
neutral values, semantic mappings, and token names from the current
design-system documentation or Figma variables. Do not create
approximate neutral tokens.

**Typography:** Swing uses **Manrope**. Confirm the exact type styles,
weights, sizes, line heights, and letter spacing from the current
typography documentation or Figma text styles. Do not substitute another
font or invent a type scale.

### Token rules

-   Prefer existing Figma variables, color styles, text styles, and
    other published tokens.
-   Use semantic tokens when they exist; do not select a raw brand color
    just because it looks close.
-   Preserve the intended light/dark theme behavior.
-   Do not introduce new colors, typography styles, spacing values,
    radii, shadows, or effects without a clear need.
-   If a required token is missing, identify the gap and ask or propose
    a clearly labeled new token for approval.
-   Never rename or overwrite shared tokens as part of an ordinary
    screen-design task.

## Component-first design

Before drawing a new UI element:

1.  Search the active Swing library and target file for an existing
    component that serves the same purpose.
2.  Inspect its variants, properties, states, dimensions, and usage.
3.  Reuse the existing component whenever it fits.
4.  Use component properties and variants rather than detaching or
    recreating components.
5.  Preserve component and layer naming conventions already used in the
    file.

Do not: - Recreate an existing Swing component from primitive shapes. -
Detach instances without a specific reason. - create duplicate
components that differ only slightly from existing ones. - invent
component names or variant properties and imply they already exist. -
change a shared library component when the task only requires a local
screen adjustment.

If no suitable component exists, compose the screen using existing
primitives and patterns. Create a new reusable component only when the
requirement justifies it. Clearly identify newly created components and
any assumptions.

## Layout and responsive behavior

-   Follow the spacing, grid, sizing, alignment, and safe-area rules
    defined in Swing's documentation and the active file.
-   Use Auto Layout and constraints appropriately so layouts remain
    maintainable.
-   Respect the existing frame dimensions and platform conventions
    unless the task specifies a different target.
-   Keep hierarchy, grouping, and alignment consistent with nearby
    approved Swing screens.
-   Avoid arbitrary pixel nudges when a layout rule or Auto Layout
    relationship is more appropriate.
-   Consider long text, localization, loading, empty, error, disabled,
    and content-overflow states where relevant.
-   Do not assume a mobile layout can simply be stretched to desktop or
    vice versa.

If exact spacing or breakpoint rules are unavailable, inspect comparable
approved screens and state any assumptions.

## Interaction and product behavior

Design the interface as a usable product experience, not just a static
picture.

-   Follow existing Swing interaction patterns and component states.
-   Represent relevant default, hover, pressed, focused, selected,
    disabled, loading, success, warning, and error states where
    applicable.
-   Make navigation, selection, form validation, feedback, and
    confirmation behavior clear.
-   Preserve the user's task context and avoid unnecessary steps.
-   Use concise, clear UI copy that fits the available space.
-   Do not invent backend behavior, payment outcomes, booking rules, or
    system capabilities. Ask for clarification when product behavior is
    not specified.

For Swing-specific flows, inspect existing product screens and
interaction documentation before proposing a new pattern.

## Figma Make instructions

When generating or editing a Swing experience in Figma Make:

1.  Understand the requested user goal, platform, screen, and flow.
2.  Consult the Swing sources and inspect available design-system
    context before implementation.
3.  Build with the closest available Swing components, variables, and
    visual patterns.
4.  Keep screens and states consistent across the complete flow.
5.  Use realistic, coherent content; avoid placeholder copy unless
    requested.
6.  Make interactive elements behave consistently with the described
    product behavior.
7.  Check layout at the intended viewport and account for content
    variation.
8.  Review the generated result against the Swing design system before
    finishing.

Do not interpret a request for a new screen as permission to redesign
the entire Swing visual language.

## Figma Design editing instructions

When working in an existing Figma Design file:

1.  Inspect the target page, frame, layers, and related components
    before editing.
2.  Preserve the existing file organization and naming conventions.
3.  Prefer editing existing instances and using approved variants.
4.  Avoid unnecessary changes to unrelated frames, pages, components, or
    library assets.
5.  Keep Auto Layout, constraints, and component relationships intact.
6.  Make only the changes required by the user's request.
7.  After editing, inspect the result for broken layouts, detached
    instances, missing styles, and inconsistent states.

Do not report an edit as completed unless the Figma operation actually
succeeded.

## Visual quality and UX review

Before presenting the result, review it against this checklist:

-   [ ] The screen serves the requested user goal.
-   [ ] The design follows the current Swing visual language.
-   [ ] Existing Swing components were reused where appropriate.
-   [ ] Colors use approved Swing variables or styles.
-   [ ] Typography uses Manrope and approved text styles.
-   [ ] Spacing, sizing, and layout follow verified Swing patterns.
-   [ ] Hierarchy, contrast, readability, and alignment are clear.
-   [ ] Interaction states and feedback are considered.
-   [ ] Copy is concise, consistent, and appropriate to the context.
-   [ ] No unrelated screens or shared components were changed.
-   [ ] No unsupported product behavior or invented design tokens were
    introduced.

Fix issues you can safely resolve before presenting the result. Mention
any remaining gaps or assumptions.

## Communication rules

When requirements are incomplete, ask only the most important clarifying
question before making consequential assumptions.

When presenting completed work, briefly summarize: - What was created or
changed. - Which existing Swing components or patterns were reused. -
Any new components, tokens, or assumptions. - Any design-system gaps
that need review.

Be transparent about limitations. Never claim full design-system
compliance if the relevant references or Figma library could not be
inspected.

## Core principle

**Swing first. Existing system before new creation. Verify before
assuming.**

Every Swing interface should feel like part of the same product
ecosystem, whether it is created in Figma Design or Figma Make.
