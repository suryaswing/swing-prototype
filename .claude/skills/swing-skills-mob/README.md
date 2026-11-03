# swing-skills-mob

**Swing Mobile Design System — an Agent Skill that keeps every AI-generated Swing Mobile
design inside the official design system.**

This skill is a **mandatory** design guideline and quality-control standard. Any AI agent
producing, modifying or prompting Swing Mobile UI/UX must read it before executing the
task — not as an optional reference.

---

## What it does

- Encodes the official Swing Mobile Design System extracted live from the
  [ADS - For Mobile](https://www.figma.com/design/ILlOBW8RpEBRmDvU6LQsx9/ADS--For-Mobile?node-id=149-4844)
  Figma file (`ILlOBW8RpEBRmDvU6LQsx9`).
- Forces a 5-step workflow: read → inspect Figma → identify components → apply standards →
  validate.
- Generates Figma Make / Figma Use prompts that contain the **actual** Swing
  specifications, not a vague "follow the design system".
- Enforces component reuse over reinvention.
- Marks anything absent from Figma as `UNDOCUMENTED` instead of inventing it.
- Requires a compliance disclosure block on every deliverable.

---

## Install

The skill is already installed in this repository in both supported locations:

```
.claude/skills/swing-skills-mob/     ← Claude Code and other .claude-based hosts
.github/skills/swing-skills-mob/     ← GitHub Copilot / VS Code
```

Both trees are identical. Update one and mirror to the other:

```bash
cp -R .claude/skills/swing-skills-mob/. .github/skills/swing-skills-mob/
```

### Other Agent Skills-compatible hosts

Copy the `swing-skills-mob/` folder into whichever location your host reads:

| Host | Project path | Personal path |
|---|---|---|
| Claude Code | `.claude/skills/swing-skills-mob/` | `~/.claude/skills/swing-skills-mob/` |
| GitHub Copilot / VS Code | `.github/skills/swing-skills-mob/` | `~/.copilot/skills/swing-skills-mob/` |
| Generic Agent Skills | `.agents/skills/swing-skills-mob/` | `~/.agents/skills/swing-skills-mob/` |

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
    ├── color-system.md                   # Brand + neutral ramps, semantic mapping
    ├── typography.md                     # Manrope scale, named Figma styles, tracking formula
    ├── spacing-layout.md                 # Padding, gaps, heights, radius, elevation, touch targets
    ├── components.md                     # 22 component sections + full library inventory
    ├── interaction-patterns.md           # States, feedback, navigation, overlays
    └── design-quality-checklist.md       # Validation procedure + disclosure block
```

References are modular and one level deep from `SKILL.md`, so an agent can load only what
the task needs.

---

## What the skill knows (verified from Figma)

| | |
|---|---|
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
2. Re-inspects the relevant pages in `ILlOBW8RpEBRmDvU6LQsx9` via Figma MCP to confirm
   the components still match.
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
- Record inconsistencies **as they are** — for example the searchbar radius is 8px at
  Medium and 12px at Large. Do not normalise them away.
- When a previously undocumented area is added to Figma, move it out of the §5 gap list.

---

## Source of truth

[ADS - For Mobile](https://www.figma.com/design/ILlOBW8RpEBRmDvU6LQsx9/ADS--For-Mobile?node-id=149-4844)
(`fileKey: ILlOBW8RpEBRmDvU6LQsx9`)

Sibling libraries `ADS: For Desktop`, `ADS: Foundations`, `Minimal_Web` and
`Eagle - Swing Design System 2.0` are **not** mobile sources.
