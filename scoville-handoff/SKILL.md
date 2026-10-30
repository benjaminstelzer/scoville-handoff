---
name: scoville-handoff
description: Create a factual continuation prompt for an explicitly requested transfer to another agent or session, including Scoville Handoff or "handoff to a new session". Ordinary Plan maintenance belongs to Plan. Do not activate for ordinary summaries, shortening, low context, wrapping up, or ending a session.
compatibility: "Agent Skills host that can read established task sources. Optional read-only Git inspection. No network or subagents. Developed for Codex and Claude Code. Python 3.11+ for the bundled text-size checker; manual fallback only without suitable Python. Helper errors do not enable fallback."
---

# Scoville Handoff

Create one copy-ready snapshot for an explicitly requested transfer of an
actual task, including empty, completed or not-started work. Questions about
Handoff or a hypothetical transfer call for an answer or assessment. If future
reuse is requested but transfer intent is unclear, ask one question before
reading sources or producing a handoff. Ordinary summaries, low context and
session endings do not activate this workflow.

## Read within the transfer scope

Finish already required and authorized pre-transfer updates through their
active owner, such as Plan for Step status, before Handoff starts. Handoff
grants no additional task authority.

Use established conversation facts and the
[continuation template](assets/continuation-prompt.md). Additional task reads
are limited to sources explicitly named or already established in the
conversation and optional read-only version-control inspection. Identify the
missing required facts, then read only the passages needed to establish them,
each completely. Do not search for new sources or restore unrelated history.

During Handoff, do not advance the task: no task edits, builds, tests, probes,
dummy or other task commands, unrelated reads, stat/list operations or external
effects. Only handoff preparation and delivery permit interpreter discovery,
temporary artifact writes, size checks and complete-file publication.

Retain each source's exact path, read scope and completeness:

| Read state | Action |
| --- | --- |
| Required passages complete | Use their established facts without rereading. |
| Required content missing | Recover only missing content through permitted ordered ranges or cursors; do not repeat an oversized request. |
| Plausibly transient failed range | Retry that range once within user read limits. |
| No progress, repeated failure or user read limit | Stop recovery; record usable facts, attempted recovery, gaps and unread ranges beside the source. |

Finish permitted recovery before composing. Label partial sources and passage
reads accurately. Conflicting revisions and material gaps block dependent
receiver verification and actions, not snapshot creation.

## Preserve continuation facts

Before requesting or reading machine reports, logs or structured state, or
composing the continuation prompt or answering a disputed factual or technical
conclusion, apply the
[shared writing rules](references/writing.md): use retained matching rules or
load them if needed, with their conditional data, shell and delivery routes.
They grant no additional task reads or actions.

Capture the template's Objective and required continuation facts: authority and
ownership, user-owned changes, accepted decisions, active sibling state,
observed results and evidence limits, blockers, hazards and next safe action.
Preserve exact identities, paths, commits, URLs, commands, errors and decisive
quotations, with assumptions, unknowns and time-sensitive details. Transfer known
material facts directly, with their source; distinguish preferences and
proposals from requirements and accepted decisions. A transfer request changes
neither task decisions nor previously granted continuation rights.

For interrupted or one-time effects, retain running handles, original producer
identity, complete stdout/stderr capture locations and completeness, and final
exit status or the exact missing evidence. Recovery must use the original
execution and evidence rather than repeat the effect.

Use `unknown` for missing information and `none known` for no known instances;
neither proves absence. Use `Status: not_started` only when established by the
conversation or an allowed task source.

For file-based work, name the task working directory established by the
conversation or an allowed canonical project source, including a task repository
already verified during the work. Otherwise use `Working directory: unknown`.
Include temporary workspace or host state only when established as task state.

Redact every secret occurrence, including quotations, warnings and replacement
instructions. Preserve established variable names as `NAME=[redacted]`.

An explicit lossless request preserves every in-scope non-secret fact. Under a
tight output limit, remove repetition and unrelated history before shortening
explanations; preserve required facts and safeguards. If necessary content still
cannot fit, use the shared complete-file route for the complete unchanged fenced
artifact, returning its absolute path and an instruction to read it entirely
before continuing.

## Compose and check the prompt

Keep the template's four H2 sections (Receiver Instructions, Objective, State
and Resume Steps), every Objective field, Status and all three Resume Steps.
Other State labels are optional; omit empty or inapplicable categories while
preserving required continuation facts and relevant unknowns. Name each source
once beside its facts, identifying conversation facts as such; repeat facts only
when needed for a hazard or first step.

Keep Receiver Instructions intact except for translation and secret redaction.
Use the requested language, otherwise the conversation language; translate
headings, labels and instructions consistently. Preserve technical identifiers,
literal markers such as `unknown` and exact quotations except secret values.
Use one outer Markdown fence with at least four backticks and more backticks
than any run inside the prompt; match its opening and closing length, including
when saving the artifact to a file.

Choose Resume Step 1 in this priority order:

| Condition | First step |
| --- | --- |
| Goal unknown, or Acceptance unknown and next action depends on it | Ask before execution or recovering a running command. |
| Known blocker | Resolve the first blocker. |
| In-flight work | Recover its state. |
| Otherwise | Take the next safe action. |

Make the remaining steps concrete and end with an observable completion
criterion. Active or incompletely accepted work names its decisive next check.
For completed work with current evidence, use the three steps only to check
current state, reconcile contradictions and confirm no material mismatch;
invent no work or repeated check to fill a step.

Check the full prompt against the captured facts, sources and template. A fresh
receiver must have the required facts, authority, next permitted action and
completion criterion without hidden history. For lossless requests, account for
every in-scope non-secret fact. Correct omissions and contradictions; remove
placeholders, secrets, invented facts and preparation-only tool details.
Return exactly the fenced artifact without surrounding text, or the specified
path and complete reading instruction for file delivery.

This Skill works independently. Other Scoville Skills are optional; use an
available, active sibling for its applicable concern. Do not install, simulate
or require an absent sibling.
Explicit activation requirements and user exclusions remain applicable.

Family owners, in suite order:

- `scoville-code`: engineering scope, implementation, risk, and validation.
- `scoville-plan`: durable Plans, Work Items, Decisions, and lifecycle state.
- `scoville-ui`: framework UI implementation and acceptance, including supported WordPress admin surfaces.
- `scoville-handoff`: active-work transfer.
- `scoville-project-context-cleanup`: requested project-rule and index wording, information quality and structure.
- `scoville-skillwriter`: Skill and reusable prompt wording for frontier models.
