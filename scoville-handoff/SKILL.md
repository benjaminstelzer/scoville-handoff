---
name: scoville-handoff
description: Create a factual continuation prompt for an explicitly requested transfer to another agent or session, including Scoville Handoff or "handoff to a new session". Ordinary Plan maintenance belongs to Plan. Do not activate for ordinary summaries, shortening, low context, wrapping up, or ending a session.
compatibility: "Agent Skills host that can read established task sources. Optional read-only Git inspection. No network or subagents. Developed for Codex and Claude Code. Python 3.11+ and the bundled text-size checker are required for output capture, size checks and delivery as a file."
---

# Scoville Handoff

Create one copy-ready snapshot for an explicitly requested transfer of an
actual task, including empty, completed or not-started work. Answer a question
about Handoff or a hypothetical transfer; produce no handoff. If future reuse
is requested but the transfer intent is unclear, ask one question before
reading sources or producing a handoff.

This Skill works on its own. When another Scoville Skill is installed and
active, use it for the concern it owns. Do not install, imitate or require an
absent one.
Do not use a Skill that needs explicit activation before it is activated, or
one the user excluded.

## Read within the transfer scope without changing the task

Before taking the snapshot, finish updates that were already required and
authorized before the transfer request through their applicable owner, such
as Plan for Step status, with the checks that owner requires for them. If an update is blocked or its Skill is excluded or
absent, record the observed state and the concrete gap in the snapshot.

Use the facts established in the conversation and the
[continuation template](assets/continuation-prompt.md). Beyond these, read
only sources named or already established in the conversation; read-only
version-control inspection is optional. Determine which required facts are
missing, then read only the passages that establish them. A handoff transfers what is
established: do not research new sources or restore unrelated history.

Creating the handoff must not change the task, because the receiver treats the
snapshot as the state at transfer. A transfer request changes no task decision
and no previously granted permission to continue. Make no task edits. Run no builds, tests,
probes or other task commands. Do no unrelated reads or stat/list operations.
Cause no external effects. Only preparing and delivering the handoff may use
interpreter discovery, temporary artifact writes, size checks and file
publication.

Handle reads as follows:

| Read state | Action |
| --- | --- |
| Required content missing | Recover only the missing content through permitted ordered ranges or cursors; do not resend an oversized request, it will fail again. |
| Plausibly transient failed range | Retry that range once within the user's read limits. |
| No progress, repeated failure or the user's read limit | End the recovery and record beside the source the usable facts, the gaps and the unread ranges. |

Finish permitted recovery before composing. Label partial sources as such.
Name conflicting revisions and material gaps: they block the receiver's
checks and actions that depend on them, not the snapshot.

## Preserve continuation facts

Capture the template's Objective and the known continuation facts:
authorization and ownership, the user's uncommitted work and whether it is
the work to continue, accepted decisions, the
active Work Item and Step, observed results and what they do not show,
blockers, hazards and the next safe action. Preserve exact paths, commits,
URLs, commands, errors and decisive quotations, with assumptions, unknowns
and time-sensitive details. State each known material fact directly. Keep
preferences and proposals apart from requirements and accepted decisions.
For a stopped or transferred Scoville Workflow, include its requirement for a
new explicit Workflow invocation before the receiver resumes execution.

Record applicable stops with their scope and the known handles of running
processes and agents. For interrupted or one-time effects, record what
originally produced the effect, the locations and completeness of stdout and stderr
captures, and the final exit status or the exact missing evidence. Recovery
uses that original run and its evidence; the effect is not repeated.

Redact every occurrence of a secret, including in quotations, warnings and
replacement instructions, and keep established variable names as
`NAME=[redacted]`.

Leave out repetition and history the receiver does not need to continue. On
an explicit lossless request, keep every in-scope non-secret fact.

## Compose and check the prompt

Keep the template's four H2 sections (Receiver Instructions, Objective, State
and Resume Steps), every Objective field, Status and one to three Resume Steps.
File-based work also requires Working directory, established by the conversation
or an allowed canonical task source. Include temporary workspace or host state
only when established as task state. Use `Status: not_started` only when
established by an allowed source. Write `unknown` for unestablished required
fields and for optional fields the next action depends on. Omit other unknown
optional labels. Omission and `unknown` carry no evidence of absence. Name each
source once, by its exact path, beside its facts and mark conversation facts
as such. Repeat a fact
where a hazard or the first step needs it.

Keep Receiver Instructions intact apart from translation and secret redaction.
Use the requested language, otherwise the conversation language, and translate
headings, labels and instructions consistently; keep literal markers such as
`unknown` untranslated. Use one outer Markdown fence with at least four
backticks and more backticks than any run inside the prompt, with matching
opening and closing length, also when the artifact is saved to a file.

Choose Resume Step 1 in this priority order:

| Condition | First step |
| --- | --- |
| Goal unknown, or Acceptance unknown and the next action depends on it | Secure the authorized original output and observe any in-flight state. Ask before the dependent action, including intervention in that run. |
| Known blocker | Resolve the first blocker. |
| In-flight work | Recover its state. |
| Otherwise | Take the next safe action. |

Add a step only for a further concrete action, up to three in all; the last
step ends with an observable completion criterion. For active or
incompletely accepted work, name its decisive next check. For completed work
with current evidence, one step that rechecks the result is enough.

Check the full prompt against what this Skill and the template require and
correct what is missing or contradictory; remove template placeholders and
tool details used only to prepare the handoff.

## Deliver the checked prompt

After a report on any other work the same request asked for, return the
checked fenced prompt. For a known output limit, size-check that complete
reply under [Output delivery](references/output-delivery.md) and follow its
result; a published file holds the fenced prompt alone.

## Shared references

Read one when its condition holds. A complete, unchanged copy in context
counts as read, including one embedded in your assignment. Fetch incomplete
or changed passages, and reload when requested.

- [Writing](references/writing.md): a plan, decision, instruction, review, handoff or a report the user asked for as the result; a disputed conclusion.
- [Machine data](references/machine-data.md): a structured report, log file or saved state you must evaluate, such as JUnit XML or coverage data; a test runner's console summary is not one.
- [Shell commands](references/shell-commands.md): composed text or scripts passed through a shell; quoting, PowerShell encoding, exact bytes or several exit statuses matter.
- [Output delivery](references/output-delivery.md): before a command whose output may exceed the display limit or is needed as evidence and cannot be reproduced; text that must fit a known limit; delivery as a file.
- [Python discovery](references/python-discovery.md): a bundled helper or other Python you run, no interpreter verified this session.
- [Instruction design](references/instruction-design.md): a reusable instruction, Skill rule or prompt template.

Family owners, in suite order:

- `scoville-code`: engineering scope, implementation, risk, and validation.
- `scoville-plan`: durable Plans, Work Items, Decisions, and lifecycle state.
- `scoville-ui`: framework UI implementation and acceptance, including supported WordPress admin surfaces.
- `scoville-handoff`: active-work transfer.
- `scoville-project-context-cleanup`: requested project-rule and index wording, information quality and structure.
- `scoville-skillwriter`: Skill and reusable prompt wording for frontier models.
