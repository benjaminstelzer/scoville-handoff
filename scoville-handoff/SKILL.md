---
name: scoville-handoff
description: Create a factual continuation prompt for an explicitly requested transfer to another agent or session, including Scoville Handoff or "handoff to a new session". Ordinary Plan maintenance belongs to Plan. Do not activate for ordinary summaries, shortening, low context, wrapping up, or ending a session.
compatibility: "Agent Skills host that can read established task sources. Optional read-only Git inspection. No network or subagents. Developed for Codex and Claude Code. Python 3.11+ for the bundled text-size checker; manual fallback only without suitable Python. Helper errors do not enable fallback."
---

# Scoville Handoff

Create one copy-ready snapshot for an explicitly requested transfer of an
actual task, including empty, completed or not-started work. A question about
Handoff or a hypothetical transfer gets an answer or assessment instead. If
future reuse is requested but the transfer intent is unclear, ask one question
before reading sources or producing a handoff. Ordinary summaries, low context
and session endings are not transfers.

## Read within the transfer scope

Updates that are already required and authorized before the transfer, such as
Plan's Step status, are finished through their owner before Handoff starts.

Use the facts established in the conversation and the
[continuation template](assets/continuation-prompt.md). Further reads are
limited to sources named or already established in the conversation and to
optional read-only version-control inspection. Identify the required facts
that are missing, then read only the passages that establish them, each
completely. A handoff transfers what is established; it does not research new
sources or restore unrelated history.

Creating the handoff must not move the task, because the receiver treats the
snapshot as the state at transfer: no task edits, builds, tests, probes or
other task commands, no unrelated reads or stat/list operations, no external
effects. Only preparing and delivering the handoff itself may use interpreter
discovery, temporary artifact writes, size checks and file publication.

Keep each source's exact path, read scope and completeness:

| Read state | Action |
| --- | --- |
| Required passages complete | Use their established facts without rereading. |
| Required content missing | Recover only the missing content through permitted ordered ranges or cursors; do not resend an oversized request, it will fail again. |
| Plausibly transient failed range | Retry that range once within the user's read limits. |
| No progress, repeated failure or the user's read limit | End the recovery and record beside the source the usable facts, the attempted recovery, the gaps and the unread ranges. |

Finish permitted recovery before composing, and label partial sources and
passage reads as such. Conflicting revisions and material gaps block the
receiver's dependent verification and actions, not the snapshot; name them.

## Preserve continuation facts

Capture the template's Objective and the required continuation facts:
authority and ownership, user-owned changes, accepted decisions, active sibling
state, observed results and evidence limits, blockers, hazards and the next
safe action. Preserve exact identities, paths, commits, URLs, commands, errors
and decisive quotations, with assumptions, unknowns and time-sensitive details.
Transfer known material facts directly with their source, and keep preferences
and proposals apart from requirements and accepted decisions. A transfer
request leaves task decisions and previously granted continuation rights as
they are.

For interrupted or one-time effects, keep running handles, the original
producer's identity, the locations and completeness of the stdout and stderr
captures, and the final exit status or the exact missing evidence. Recovery
uses the original execution and its evidence; the effect is not repeated.

Use `unknown` for missing information and `none known` for no known instances;
neither proves absence. Use `Status: not_started` only when the conversation or
an allowed task source establishes it.

For file-based work, name the task working directory established by the
conversation or an allowed canonical project source, including a task
repository already verified during the work; otherwise write
`Working directory: unknown`. Include temporary workspace or host state only
when it is established as task state.

Redact every occurrence of a secret, including in quotations, warnings and
replacement instructions, and keep established variable names as
`NAME=[redacted]`.

An explicit lossless request preserves every in-scope non-secret fact. Under a
tight output limit, remove repetition and unrelated history before shortening
explanations, and keep required facts and safeguards. If necessary content
still cannot fit, publish the complete unchanged fenced artifact as a file
and return its absolute path with the instruction to read it entirely before
continuing.

## Compose and check the prompt

Keep the template's four H2 sections (Receiver Instructions, Objective, State
and Resume Steps), every Objective field, Status and all three Resume Steps.
Other State labels are optional: omit empty or inapplicable categories while
keeping required continuation facts and relevant unknowns. Name each source
once beside its facts and mark conversation facts as such; repeat a fact only
where a hazard or the first step needs it.

Keep Receiver Instructions intact apart from translation and secret redaction.
Use the requested language, otherwise the conversation language, and translate
headings, labels and instructions consistently. Preserve technical identifiers,
literal markers such as `unknown` and exact quotations except secret values.
Use one outer Markdown fence with at least four backticks and more backticks
than any run inside the prompt, with matching opening and closing length, also
when the artifact is saved to a file.

Choose Resume Step 1 in this priority order:

| Condition | First step |
| --- | --- |
| Goal unknown, or Acceptance unknown and the next action depends on it | Ask before execution or before recovering a running command. |
| Known blocker | Resolve the first blocker. |
| In-flight work | Recover its state. |
| Otherwise | Take the next safe action. |

Make the remaining steps concrete and end with an observable completion
criterion. Active or incompletely accepted work names its decisive next check.
For completed work with current evidence, the three steps check the current
state, reconcile contradictions and confirm that no material mismatch exists;
they are not filled with invented work or repeated checks.

Check the full prompt against the captured facts, sources and template. A
fresh receiver must have the required facts, authority, next permitted action
and completion criterion without hidden history. For a lossless request,
account for every in-scope non-secret fact. Correct omissions and
contradictions, and remove placeholders, secrets, invented facts and
preparation-only tool details. Return exactly the fenced artifact without
surrounding text, or the path and complete reading instruction for file
delivery.

## Shared references

Read one when its condition holds. A complete copy already in context from
this build, including one embedded in your assignment, counts as read; read it
again when it is incomplete or uncertain or a reload is requested.

- [Writing](references/writing.md): a plan, decision, instruction, review, handoff or report; a disputed conclusion.
- [Machine data](references/machine-data.md): a test report, log or structured state as a result.
- [Shell commands](references/shell-commands.md): composed text or scripts passed through a shell; quoting, PowerShell encoding, exact bytes or several exit statuses matter.
- [Output delivery](references/output-delivery.md): before a command whose output may exceed the display limit or whose effect or result cannot be repeated; text that must fit a known limit; delivery as a file.
- [Python discovery](references/python-discovery.md): a Python command or bundled helper, no interpreter verified this session.
- [Instruction design](references/instruction-design.md): a reusable instruction, Skill rule or prompt template.

This Skill works on its own. Use another Scoville Skill for its concern when
it is installed and active; an absent one is neither installed, imitated nor
required.
A Skill that needs explicit activation stays out until it is activated, and
one the user excluded stays out.

Family owners, in suite order:

- `scoville-code`: engineering scope, implementation, risk, and validation.
- `scoville-plan`: durable Plans, Work Items, Decisions, and lifecycle state.
- `scoville-ui`: framework UI implementation and acceptance, including supported WordPress admin surfaces.
- `scoville-handoff`: active-work transfer.
- `scoville-project-context-cleanup`: requested project-rule and index wording, information quality and structure.
- `scoville-skillwriter`: Skill and reusable prompt wording for frontier models.
