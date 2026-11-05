---
name: swing-prd-review
description: "Review Swing product requirements before UI/UX design. Use when validating a PRD, finding edge cases, generating discovery or clarification questions, checking user flows, or deciding whether a feature is ready to design. Reuse verified decisions and lessons from prior Swing cases, and record confirmed outcomes so future reviews improve."
argument-hint: 'Share the PRD or feature requirements to review before design'
---

# Swing PRD Readiness Review

Review the PRD primarily as an end-to-end user and system flow. First make the happy
path clear, then walk each step to find realistic alternate, interrupted, and failure
cases the happy path does not cover. Surface only a short business perspective when a
gap affects the feature's goals, success measures, operational ownership, or material
product risk. Do not invent product behavior or silently fill gaps.

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

Summarize the feature in plain language, identify each actor, and map the primary
happy-path flow from entry point to observable completion. Include user actions and
system responses at each step. Then note any alternate paths that the PRD explicitly
defines.

Extract only the business context needed to interpret the flow:

- The user or product outcome the flow is meant to achieve.
- A success metric, operational dependency, or policy constraint that changes flow
  behavior, if present.
- Explicit exclusions that define what the flow must not promise.

Do not turn this into a general business strategy review. Keep findings traceable to a
PRD section, requirement ID, or verified precedent; label new observations as reviewer
questions.

### Step 4 — Challenge the PRD with scenarios

Walk the happy path in order. At every step, ask what happens when the user changes
their mind, cannot continue, submits unexpected data, loses access/network, receives a
failure or stale result, or re-enters after state has changed. Check relevant state
transitions, permissions, duplicates/concurrency, notifications, and recovery paths.
Consider accessibility, localization, and platform constraints only where they can
change the flow or its completion.

Prioritize cases that alter the user's next step, risk data loss or duplicate action,
create an unrecoverable state, expose private information, or contradict another PRD
rule. Do not enumerate generic edge-case categories that have no plausible connection
to this feature. For each gap, state the expected behavior only if the PRD or a
confirmed source specifies it; otherwise write “not specified” and turn it into a
question.

Use [references/review-framework.md](./references/review-framework.md) to structure the
flow map and select relevant off-happy-path scenarios.

### Step 5 — Ask prioritized, answerable questions

Ask questions that resolve a flow decision, not cosmetic preferences that can wait
until design. Group questions by the point in the flow where they arise and include:

- **Priority:** Blocker, Important, or Later.
- **Question:** one clear decision at a time.
- **Why it matters:** the affected user path, state, or requirement.
- **Options / example:** only when they help the product owner decide; do not imply an
  option is already approved.
- **Evidence:** the source that raised the question, or “not specified in the PRD”.

Ask the smallest useful batch. Put design-blocking questions first, then order the rest
by flow progression. Mention business impact briefly only when the question affects an
explicit goal, metric, operating SLA, or material risk. Avoid asking a question already
answered by an authoritative, current source.

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

Use this flow-first structure unless the user asks for another format:

1. **PRD understanding** — short feature summary and scope.
2. **Historical context** — relevant prior cases, their evidence/status, or “no relevant
   verified case found”.
3. **Happy-path flow** — concise ordered steps from entry to completion, including
   actors and system responses.
4. **Potential cases outside the happy path** — grouped under the flow step they affect;
   include scenario, specified behavior or gap, and priority/risk.
5. **Questions before design** — prioritized and ordered by flow progression. Include
   why the decision matters and evidence.
6. **Business perspective** — brief and only where directly relevant: impact on stated
   goal/metric, operational dependency, or material risk. Omit if none.
7. **Readiness verdict** — one of the three defined outcomes, with rationale.
8. **Learning to retain** — confirmed rule/case to add, or confirmation still needed.

Do not make up expected behavior for missing requirements. Use “not specified” and turn
the gap into a question.

Keep the happy-path summary short; spend most of the review on meaningful deviations
from it.

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
- **Flow-first:** the happy path is a map for discovering plausible off-path scenarios,
  not the whole review.
- **Business-light:** connect findings to stated business outcomes when useful without
  turning the review into a broad strategy or financial assessment.
- **Historically aware:** prior cases inform the review without overriding current
  approved requirements.
- **Actionable:** the team can answer the questions and know whether design can start.
- **Honest:** inaccessible sources, uncertainty, stale precedents, and untested areas are
  disclosed.
