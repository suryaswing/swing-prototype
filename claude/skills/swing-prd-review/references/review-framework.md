# PRD Review Framework

Use this as a scenario generator, not as a requirement to enumerate every row. Begin
with the PRD's happy path and select only cases that plausibly interrupt or change a
step, state, outcome, or recovery path. Keep business analysis brief and tied to the
feature's stated goals, metrics, and operating constraints.

## Flow-first review method

1. Write the main success path as numbered steps from entry to observable completion.
   At each step, name the actor's action and the system response.
2. Walk the flow in order. For each step, consider only relevant deviations: user
   cancels or goes back; preconditions fail or permissions change; input is missing,
   invalid, duplicated, or at a boundary; a request is slow, interrupted, retried, or
   fails; state changes elsewhere; or the user returns to a stale/incomplete flow.
3. Trace meaningful outcomes to the next step. Check that alternate states have a
   defined owner, allowed action, exit/recovery path, and user-visible result where
   applicable.
4. Record what the PRD says. If behavior is absent or conflicting, mark it as such and
   ask a decision question; do not design the missing rule on the product owner's
   behalf.
5. Prioritize cases that affect completion, data integrity, access/privacy, irreversible
   actions, or a stated success/operational commitment. Omit generic cases with no
   credible connection to this flow.

## Requirement-to-scenario matrix

| Area | Prompts to test | Typical PRD gap |
|---|---|---|
| Actors and access | Who can start, view, edit, approve, or cancel? What if role/access changes mid-flow? | Roles, permissions, or ownership unclear |
| Entry and preconditions | Where does the flow start? What must already exist? Can it be opened from multiple entry points? | Entry conditions or context missing |
| Main path | What does the user do, what does the system do, and what proves completion? | Acceptance criteria describe UI but not outcome |
| Alternate path | Can the user skip, cancel, go back, save a draft, or resume later? | Exit and resume behavior missing |
| Input and validation | Required/optional fields, format, minimum/maximum, whitespace, unsupported characters, duplicates, validation timing | Field rules or error recovery unspecified |
| Boundaries and volume | Minimum/maximum values, zero items, one item, many items, long content, limits reached | Boundary behavior absent |
| Empty and first use | What does a new user see? What if there are no results, records, or choices? | Empty state or next action undefined |
| Loading and interruption | Slow response, offline, timeout, app backgrounded, navigation away during save | Progress, cancellation, and retry undefined |
| Failure and recovery | Server error, partial failure, conflict, unavailable dependency, retry, data preservation | Error copy/action and recovery path missing |
| Duplicate and concurrency | Double tap, repeated request, same item changed elsewhere, stale data | Idempotency and conflict behavior unclear |
| State and lifecycle | Draft, pending, approved, rejected, expired, archived, deleted; transitions and reversibility | State machine or transition authority missing |
| Notifications | What is sent, to whom, when, through which channel, and what if delivery fails? | Trigger, audience, or delivery semantics absent |
| Privacy and data | Visibility, consent, retention, deletion, sensitive data exposure | Data rules or user control absent |
| Accessibility and locale | Keyboard, screen reader, large text, RTL, translated/long strings, local formats | Behavior under accessibility/locale constraints unknown |
| Analytics and success | What event or outcome measures success? What is out of scope? | No measurable acceptance or success criteria |

Business review is intentionally lightweight: mention a goal, metric, operational
dependency, or business risk only when it clarifies why a flow decision matters. Do not
expand into market sizing, pricing, revenue modeling, or strategy unless requested.

## Edge-case table format

| Flow step / source | Off-happy-path scenario | Expected behavior or gap | Status | Priority |
|---|---|---|---|---|
| Step 2, PRD §X | Concrete user/system condition | Exact behavior, or “not specified” | Specified / Missing / Conflict | Blocker / Important / Later |

Use **Conflict** when two authoritative sources disagree. Include both sources; do not
choose one silently.

Group these rows by flow step. State “not applicable” only when a category was
considered and genuinely does not apply; do not pad the report with a checklist of
unrelated scenarios.

## Question prioritization

### Blocker

An answer changes the core flow, actor permissions, business outcome, data handling,
error recovery, or acceptance criteria. Do not present a production-ready design until
resolved.

### Important

An answer affects a significant alternate path or state but can be explored in a clearly
labelled, reversible prototype.

### Later

The answer can be deferred without invalidating the flow or creating misleading
behavior. Examples may include final microcopy or non-critical visual preferences.

## Before-design stop conditions

Recommend **Not ready to design** when any of these are unresolved and materially apply:

- The target actor or permission to perform the action is unclear.
- The core success outcome or completion criteria are unclear.
- A high-impact decision (e.g. visibility, approval, payment, eligibility, or data
  retention) is absent or conflicting.
- A failure can cause data loss, duplicate action, or irreversible user impact and the
  PRD gives no recovery behavior.
- The proposed design would require inventing a product rule.

If the user explicitly chooses to proceed, call the result an exploratory prototype and
list its assumptions.
