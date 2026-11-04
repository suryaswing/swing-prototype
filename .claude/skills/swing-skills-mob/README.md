# swing-skills-mob

**Swing Mobile Design System — an Agent Skill that keeps every AI-generated Swing Mobile
design inside the official design system.**

This skill is a **mandatory** design guideline and quality-control standard. Any AI agent
producing, modifying or prompting Swing Mobile UI/UX must read it before executing the
task — not as an optional reference.

---

## What it does

- Uses [ADS - Foundations](https://www.figma.com/design/JDN6zpJA4feGSY8ZcQMQeM/ADS--Foundations?node-id=8-12868)
  (`JDN6zpJA4feGSY8ZcQMQeM`) for visual foundations and
  [ADS - For Mobile](https://www.figma.com/design/ILlOBW8RpEBRmDvU6LQsx9/ADS--For-Mobile?node-id=149-4844)
  (`ILlOBW8RpEBRmDvU6LQsx9`) for mobile components, layout, and states.
- Forces a 5-step workflow: read → inspect Figma → identify components → apply standards →
  validate.
- Generates Figma Make / Figma Use prompts that contain the **actual** Swing
  specifications, not a vague "follow the design system".
- Enforces component reuse over reinvention.
- Allows bounded creativity: new component and interaction-pattern roles may account for
  about 30% of a design when existing Swing patterns do not fit, with the proposal clearly
  labelled and token-consistent.
- Marks anything absent from Figma as `UNDOCUMENTED` instead of inventing it.
- Requires a compliance disclosure block on every deliverable.
- Pairs with [`swing-prd-review`](../swing-prd-review/README.md): review a provided PRD
  for flows, edge cases, and open questions before applying visual design standards.

---

## Install

The skill is installed in this repository as a single source of truth:

```
.claude/skills/swing-skills-mob/     ← Claude Code and other .claude-based hosts
```

### Other Agent Skills-compatible hosts

Copy the `swing-skills-mob/` folder into whichever location your host reads:

| Host | Project path | Personal path |
|---|---|---|
| Claude Code | `.claude/skills/swing-skills-mob/` | `~/.claude/skills/swing-skills-mob/` |
| GitHub Copilot / VS Code | Use a supported skill discovery location | `~/.copilot/skills/swing-skills-mob/` |
| Generic Agent Skills | `.agents/skills/swing-skills-mob/` | `~/.agents/skills/swing-skills-mob/` |

This repository intentionally does not keep a duplicate `.github/skills/` copy. If a
host does not discover `.claude/skills/`, install the skill in that host's personal
location rather than adding a second copy to this repository.

The folder name **must** remain `swing-skills-mob` — it has to match the `name` field in
`SKILL.md` frontmatter. A mismatch fails silently.

---

## Verify it was discovered

1. **Claude Code** — start a session in this repo and type `/`; `swing-skills-mob` should
   appear in the skill list. Skills are also auto-loaded when the description matches the
   request.
2. **VS Code / Copilot** — open Copilot Chat and type `/`. The skill appears as a slash
   command. Check the agent-customization skill list if it does not.
3. **Quick sanity check** — ask: *"Which skill governs Swing Mobile UI design?"* The agent
   should name `swing-skills-mob` and describe the 5-step workflow.

If it does not appear, check the usual silent YAML failures: `name` not matching the
folder, an unquoted colon in `description`, or tabs instead of spaces in the frontmatter.

---

## Contents

```
swing-skills-mob/
├── SKILL.md                              # Mandatory workflow, prompt rules, non-negotiables
├── README.md                             # This file
└── references/
    ├── design-tokens.md                  # START HERE — cross-file index + quick-reference tables
    ├── design-foundations.md             # Foundations file map, verified values and source hierarchy
    ├── color-system.md                   # Brand + neutral ramps, semantic mapping
    ├── typography.md                     # Manrope scale, named Figma styles, tracking formula
    ├── spacing-layout.md                 # Padding, gaps, heights, radius, elevation, touch targets
    ├── components.md                     # 22 component sections + full library inventory
    ├── interaction-patterns.md           # States, feedback, navigation, overlays
    ├── icon-logo-usage.md                # Finding, documenting and using verified brand assets
    └── design-quality-checklist.md       # Validation procedure + disclosure block
```

References are modular and one level deep from `SKILL.md`, so an agent can load only what
the task needs.

---

## What the skill knows (verified from Figma)

| | |
|---|---|
| Foundation source | `ADS: Foundations` — palette, elevation, iconography, brand/logo assets |
| Mobile component source | `ADS: For Mobile` — mobile components, layout, typography usage, interaction states |
| Canonical artboard | 375 × 812 (iPhone 11 Pro / X) |
| Content width | 343px |
| Typeface | Manrope (ExtraBold 800 / Bold 700 / Regular 400) |
| Primary colour | `PURPLE/500 #5C00E6` · pressed `PURPLE/600 #4900B8` |
| Neutral ramp | `#1C1C28` → `#28293D` → `#555770` → `#8F90A6` → `#C7C9D9` → `#E4E4EB` → `#F2F2F5` → `#FAFAFC` → `#FFFFFF` |
| Semantic | Error `#FF2A12` · Warning `#FF8113` · Success `#36B37E` · Info `#8F90A6` |
| Radius scale | 4 / 8 / 12 / 100px |
| Elevation | `Small 0 2px 8px rgba(0,0,0,.08)` · `Large 0 16px 24px rgba(0,0,0,.22)` |
| Touch target | 48 × 48px minimum |
| Documented components | Button, Text field, Select field, Radio, Checkbox, Toggle, Searchbar, Card, Badge, Tag, Text caption, Bottom Navigation, Tab, Page header, Modal, Tooltip, Toaster, Loader, Avatar, Iconography |

---

## What it deliberately does **not** know

These are absent from the Figma library and the skill marks them `UNDOCUMENTED` rather
than guessing: grid/column system, responsive & breakpoint rules, semantic token aliases,
dark mode, motion & transitions, gestures, haptics, accessibility rules, icon grid, empty
states, toast timing, safe-area insets.

Full list: [design-quality-checklist.md §5](./references/design-quality-checklist.md).

---

## Example activation

**Request:** *"Generate a Figma Make prompt for a Swing Mobile booking confirmation screen."*

**Without the skill** the agent produces a generic screen with invented colours and fonts.

**With the skill** the agent:

1. Reads `SKILL.md` → loads `design-tokens.md`, `components.md`, `spacing-layout.md`.
2. Re-inspects relevant foundation tokens/assets in `JDN6zpJA4feGSY8ZcQMQeM` and mobile
   components in `ILlOBW8RpEBRmDvU6LQsx9` via Figma MCP.
3. Selects existing components — e.g. `Page header / Standard` (`Type=Title only,
   Title placement=Left`), `Card / Standard`, `Button / Actions` — instead of drawing new
   ones.
4. Emits a prompt containing real values:

   ```
   Screen title: Manrope ExtraBold 800, 18px / 22px, letter-spacing -0.36px (Heading/H5)
   Primary button: bg #5C00E6, CTA/Button Large, px 24px py 14px, radius 8px
   Card: bg #FFFFFF, radius 4px, Elevation Small 0 2px 8px rgba(0,0,0,0.08)
   Content width 343px · touch targets ≥ 48 × 48px · Manrope only
   ```

5. Runs the design-quality checklist and appends the compliance disclosure block, naming
   reused components, new components (if any), deviations, and anything it could not
   validate.

---

## Maintaining this skill

- Values come from Figma MCP, never from memory. When re-extracting, cite the source node
  ID alongside the value.
- Use `ADS: Foundations` for foundation tokens and brand assets, then verify usage in
  `ADS: For Mobile`; the foundation palette alone does not establish a mobile component
  variant.
- Record inconsistencies **as they are** — for example the searchbar radius is 8px at
  Medium and 12px at Large. Do not normalise them away.
- When a previously undocumented area is added to Figma, move it out of the §5 gap list.
- Figma changes do not update these references automatically. To refresh one, ask the
  agent: *"Update `swing-skills-mob` from this Figma component"* and share its node link.
  The agent should inspect the live component, compare it with the docs, update only
  affected references, keep `.claude/skills/` as the only repository copy, and report
  what changed.
- Provide edit access to the repository and view access to the Figma library. No commit
  or push is made unless requested.

---

## Source of truth

[ADS - Foundations](https://www.figma.com/design/JDN6zpJA4feGSY8ZcQMQeM/ADS--Foundations?node-id=8-12868)
(`fileKey: JDN6zpJA4feGSY8ZcQMQeM`) defines foundation assets and primitives.
[ADS - For Mobile](https://www.figma.com/design/ILlOBW8RpEBRmDvU6LQsx9/ADS--For-Mobile?node-id=149-4844)
(`fileKey: ILlOBW8RpEBRmDvU6LQsx9`) defines mobile-specific components and behavior.

Sibling libraries `ADS: For Desktop`, `Minimal_Web`, and
`Eagle - Swing Design System 2.0` are not substitutes for these sources.
