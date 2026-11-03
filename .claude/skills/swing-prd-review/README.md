# swing-prd-review

An Agent Skill for checking Swing PRDs before design: it maps requirements to real
scenarios, finds edge cases, asks prioritized questions, and gives a design-readiness
verdict.

## How it works with Swing design

Use `swing-prd-review` first for product behavior and requirement gaps. When the PRD is
ready—or the user explicitly accepts tracked assumptions—use `swing-skills-mob` for the
Swing Mobile visual system and Figma workflow.

## Install locations

This skill is installed in both project locations:

```text
.claude/skills/swing-prd-review/   # Claude Code and compatible hosts
.github/skills/swing-prd-review/  # GitHub Copilot / VS Code
```

Keep the two copies identical when updating. The `name` in `SKILL.md` must match the
folder name.

## Historical learning

`references/casebook.md` is a small, persistent project casebook. Agents should read
relevant cases before reviewing and add concise lessons only after outcomes are confirmed.
It distinguishes confirmed decisions from observed behavior and unconfirmed suggestions,
so a past AI assumption cannot accidentally become product policy.

The casebook begins with one explicitly unconfirmed workflow lesson from a prior
Community-form request. No PRD or approved product rule was available for that request.

## Example

Ask:

> Review this PRD before design. Find edge cases, compare it with prior Swing cases,
> generate the questions we need to answer, and tell me whether it is ready to design.

The skill returns a requirement-to-scenario table, prioritized questions, a readiness
verdict, and any confirmed learning worth preserving.
