# Swing Product Casebook

This file is durable, human-reviewable project memory for PRD reviews. It is not a
substitute for an approved PRD, and it does not train the model. Read relevant entries
before a review and update only after a product owner confirms the outcome.

## Evidence and status rules

- **Confirmed** — decision or outcome explicitly approved by the user/product owner or
  captured in an authoritative, current product document.
- **Observed** — behavior seen in a shipped product or existing design; intent has not
  been confirmed.
- **Unconfirmed** — proposal, open question, or past AI-generated suggestion. Never use
  as product policy.
- Mark stale entries when a newer source supersedes them. Keep the old source trail.
- Store only concise, de-identified summaries. Do not paste raw PRDs, user data, or
  secrets.

## Case index

No confirmed product decisions or completed PRD-review cases have been recorded yet.
The prior Community-form design request is retained below only as an unconfirmed
workflow lesson; it is not a product requirement.

## Unconfirmed workflow lesson: Community form request

- **Status:** Unconfirmed; not product policy.
- **Context:** A request asked for a “form daftar community” to be designed in the
  Community Figma file. No PRD was provided in the available conversation.
- **Ambiguity discovered:** “Daftar community” could mean creating a new Community or
  requesting to join an existing one. The prior design prompt assumed creation and
  suggested fields and visibility options without PRD evidence.
- **Review lesson:** Before designing, ask whether the flow is create or join; obtain the
  actor, entry point, required data, membership/approval rules, visibility, and submit
  outcome. Treat any proposed field or option as an assumption until confirmed.
- **Source:** Prior conversation in this repository's Copilot session, 2026-11-03.
- **Promotion condition:** Product owner confirms the intended flow and rules, ideally
  with a current PRD or decision record.

## Add future cases below

Use this template for each confirmed or useful case:

```markdown
### <Short feature / lesson title>

- **Status:** Confirmed / Observed / Unconfirmed
- **Domain:** <feature area>
- **Source:** <PRD ID/version, issue/PR, design, or user confirmation + date>
- **Context:** <short, de-identified summary>
- **Scenario / edge case:** <what happened or was missing>
- **Confirmed rule / outcome:** <decision; use “not confirmed” if unresolved>
- **Reusable lesson:** <how a future PRD review should change>
- **Supersedes / stale when:** <newer source or “none known”>
```
