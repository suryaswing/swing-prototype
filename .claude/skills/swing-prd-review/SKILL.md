---
name: swing-prd-review
description: "Review Swing product requirements before UI/UX design. Use when validating a PRD, finding edge cases, generating discovery or clarification questions, checking user flows, or deciding whether a feature is ready to design. Reuse verified decisions and lessons from prior Swing cases, and record confirmed outcomes so future reviews improve."
argument-hint: 'Share the PRD or feature requirements to review before design'
---

# Swing PRD Readiness Review

Review the product requirements before designing. The goal is to expose missing
decisions, test the PRD against real user and system scenarios, and help the team reach
design readiness—not to invent product behavior or silently fill gaps.

This skill complements `swing-skills-mob`:

- Use this skill **first** to review the PRD, flows, edge cases, and open questions.
- Once the PRD is ready (or the user explicitly accepts documented assumptions), use
  `swing-skills-mob` to design within the Swing Mobile Design System.

## 1. When to activate

Activate this skill before design when the user asks to:

- Review, validate, challenge, or test a PRD or product brief.
- Find edge cases, alternate paths, failure states, or missing requirements.
- Generate questions to ask before starting UI/UX design.
- Check whether a feature, user flow, or screen is ready to design.
- Compare a new proposal with prior product decisions or cases.

If a design request has no PRD, ask for one or offer a short requirements-discovery
interview before creating the design. Do not block a user who explicitly wants to
prototype; label unresolved points as assumptions and keep them easy to change.

## 2. Mandatory workflow

### Step 1 — Gather the source material

Identify the PRD, linked design/spec documents, and relevant feature context. Read
available material in the current workspace or sources the user provides. Do not claim
to have reviewed an inaccessible file, workspace, ticket, or conversation.

If there is no PRD, state that clearly and offer to elicit the missing requirements.
Separate what the document says from what the reviewer infers.

### Step 2 — Learn from verified history

Before analyzing, search the available project materials for relevant prior cases:

1. Read the casebook at [references/casebook.md](./references/casebook.md).
2. Search relevant PRDs, product decisions, user stories, changelogs, and issue/PR
   discussions available in the workspace or connected tools.
3. Prefer cases from the same feature/domain and the newest confirmed product decisions.
4. Record the source, date/version, and confidence for every historical precedent used.

Classify historical evidence as:

- **Confirmed rule** — explicit in an approved PRD or confirmed by the user/product
  owner.
- **Observed behavior** — present in an existing product or shipped design, but not
  necessarily an intended rule.
- **Unconfirmed precedent** — an earlier proposal or discussion without approval.

Use confirmed rules as constraints. Treat observed behavior as evidence to verify.
Never turn an unconfirmed proposal, a past AI suggestion, or a single anecdote into
product policy. If sources conflict, surface the conflict and ask which source governs.

### Step 3 — Model the requirements

Summarize the feature in plain language and extract:

- Target users/actors and their goals.
- Entry points, preconditions, permissions, and relevant account states.
- Main success path and expected outcome.
- Data entered, created, changed, or exposed.
- Business rules, limits, and acceptance criteria.
- Dependencies, integrations, notifications, and system-owned behavior.
- Explicit exclusions and unresolved decisions.

Use a traceable map: each finding should point to a PRD section, requirement ID,
existing product behavior, or be labelled as a reviewer question.

### Step 4 — Challenge the PRD with scenarios

For each meaningful requirement, consider the applicable scenarios in
[references/review-framework.md](./references/review-framework.md). At minimum, check:

- Alternate routes and user cancellation/back-navigation.
- Empty, partial, malformed, duplicate, or boundary-value input.
- Validation timing, correction, and recovery after an error.
- Loading, retry, timeout, offline, and service failure.
- Permission denied, expired session, and changed user/account status.
- Re-entry, duplicate submission, and concurrent/stale data.
- Success, confirmation, and what happens next.
- Accessibility, localization, and platform constraints when they affect behavior.

Do not force irrelevant categories into every review. State which areas were not
applicable or could not be verified.

### Step 5 — Ask prioritized, answerable questions

Ask questions that resolve product behavior, not cosmetic preferences that can wait
until design. For each question include:

- **Priority:** Blocker, Important, or Later.
- **Question:** one clear decision at a time.
- **Why it matters:** the affected user path, state, or requirement.
- **Options / example:** only when they help the product owner decide; do not imply an
  option is already approved.
- **Evidence:** the source that raised the question, or “not specified in the PRD”.

Ask the smallest useful batch. Put design-blocking questions first. Avoid asking a
question already answered by an authoritative, current source.

### Step 6 — Give a readiness verdict

Choose one:

- **Ready to design** — no unresolved product decisions materially change the flow.
- **Ready with tracked assumptions** — remaining gaps can be safely explored in a
  reversible prototype and are explicitly accepted as assumptions.
- **Not ready to design** — one or more unanswered decisions change core behavior,
  permissions, data, or success criteria.

Provide a short rationale and state what must be answered to move forward. Do not
describe a PRD as “validated” merely because a checklist was completed.

### Step 7 — Update the learning record

After the user or product owner confirms a decision or a case outcome:

- Add a concise, de-identified entry to [references/casebook.md](./references/casebook.md)
  using its template.
- Preserve the source and status; record the date or PRD/version when known.
- Capture reusable rules, the edge case, the confirmed resolution, and how it changes
  future reviews.
- Do not save raw PRDs, personal data, secrets, or unapproved assumptions.
- Do not promote a proposal to a confirmed rule until it is explicitly confirmed.

If no outcome has been confirmed, leave the case unpromoted and say what confirmation is
needed. Treat the casebook as project-maintained memory, not model training: agents only
benefit from it when they can read the file.

## 3. Expected review output

Use this structure unless the user asks for another format:

1. **PRD understanding** — short feature summary and scope.
2. **Historical context** — relevant prior cases, their evidence/status, or “no relevant
   verified case found”.
3. **Requirement-to-scenario review** — table with requirement/source, scenario,
   expected behavior, and status (specified / missing / conflicting).
4. **Edge cases** — prioritized and grouped by user flow or failure mode.
5. **Questions before design** — Blocker, Important, Later.
6. **Readiness verdict** — one of the three defined outcomes, with rationale.
7. **Learning to retain** — confirmed rule/case to add, or confirmation still needed.

Do not make up expected behavior for missing requirements. Use “not specified” and turn
the gap into a question.

## 4. Relationship to design work

When the user proceeds to design:

- Carry confirmed PRD rules and accepted assumptions into the design brief.
- Keep unresolved questions visible; do not hide them in UI copy or interaction choices.
- If the user asks to proceed while the PRD is not ready, make the prototype exploratory,
  identify the decisions it assumes, and avoid presenting those decisions as approved.
- Then follow `swing-skills-mob` for Swing-specific Figma inspection, component reuse,
  tokens, and visual validation.

## 5. Quality bar

A useful review is:

- **Traceable:** findings map to source evidence or are explicitly reviewer-generated.
- **Specific:** questions describe a decision and its impact.
- **Risk-based:** core behavior and costly-to-change gaps outrank polish.
- **Historically aware:** prior cases inform the review without overriding current
  approved requirements.
- **Actionable:** the team can answer the questions and know whether design can start.
- **Honest:** inaccessible sources, uncertainty, stale precedents, and untested areas are
  disclosed.
