# swing-prd-review

An Agent Skill for reviewing Swing PRDs before design: it maps the happy path
end-to-end, finds relevant cases outside that path, asks prioritized flow questions,
and gives a design-readiness verdict. Business considerations are included briefly when
they clarify an explicit goal, metric, or operational risk.

## How it works with Swing design

Use `swing-prd-review` first for product behavior and requirement gaps. When the PRD is
ready—or the user explicitly accepts tracked assumptions—use `swing-skills-mob` for the
Swing Mobile visual system and Figma workflow.

## Install locations

This skill is installed in both project locations:

The repository copy is `.claude/skills/swing-prd-review/`. Install a copy in another
host-specific discovery path only when that host does not discover the repository
location; avoid maintaining duplicate repository copies. The `name` in `SKILL.md` must
match the folder name.

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

The skill returns a concise happy-path map, off-happy-path cases grouped by flow step,
prioritized questions, a readiness verdict, and any confirmed learning worth preserving.
