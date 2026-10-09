---
name: scoville-handoff
description: Create a factual continuation prompt for an explicitly requested transfer to another agent or session, including Scoville Handoff or "handoff to a new session". Ordinary Plan maintenance belongs to Plan. Do not activate for ordinary summaries, shortening, low context, wrapping up, or ending a session.
compatibility: "Agent Skills host that can read established task sources. Optional read-only Git inspection. No network or subagents. Developed for Codex and Claude Code; other hosts untested. Python 3.11+ for the bundled text-size checker; manual fallback only without suitable Python. Helper errors do not enable fallback."
---

# Scoville Handoff

Give the receiver accurately labeled context to continue safely from one
copy-ready snapshot. An explicit transfer applies even when work is empty,
completed or not started. Without a transfer request, perform the requested
task without a handoff. If future reuse is requested but transfer intent is
unclear, ask one question before reading sources or producing a handoff.
When asked to explain or assess a hypothetical handoff, answer that question.
Produce the continuation artifact only for a requested transfer of an actual
task.

## Read within the transfer scope

Any already required and authorized pre-transfer update belongs to its active
owner, such as Plan for Step status, and must finish before Handoff starts.
The transfer request grants no additional editing authority.

Use task facts already established in the conversation. Additional reads are
limited to sources explicitly named or already established as task sources in
the conversation, optional read-only version-control inspection, and the
[continuation template](assets/continuation-prompt.md). Do not search for more
sources. Throughout this workflow, do not advance the task: no edits, builds,
tests, probes, dummy or other task commands, unrelated reads, stat or list
operations, or external effects.
Missing facts do not authorize additional actions. Only for preparing and
delivering this handoff, interpreter discovery, temporary artifact writes,
size checks and complete-file publication are permitted. This exception
grants no task edits, tests or other task commands.

Retain each source's exact path and read state:

| Read state | Action |
| --- | --- |
| Complete | Use the established facts. |
| Partial | Read permitted ordered ranges or cursors within their limits. Never attempt an oversized read or recover text after truncation. |
| Failed range, plausibly transient | Retry that range once; explicit user read limits prevail. |
| No progress, repeated failure or read limit | Stop recovery. Preserve usable facts, recovery, gaps and unread ranges beside the source. A partial source is not wholly unavailable. |

1. Finish the permitted recovery sequence before composing, including stopping
   when the table requires it; do not defer these attempts to the receiver.
2. Compose the snapshot from usable facts, preserving each source's read state,
   recovery, gaps and unread ranges. Never label a partial source complete.
3. Conflicting source revisions and material unread ranges block receiver
   verification and actions that depend on them, not snapshot creation.

## Preserve continuation facts

Read the [shared writing rules](references/writing.md) when composing the
continuation prompt. They govern wording, not permission to read more task
sources. Select the relevant continuation facts below.

Capture the goal, deliverable, acceptance, scope and authority, canonical
owners, user-owned changes, accepted decisions, active work and running handles,
observed evidence and its limits, blockers, hazards and next safe action.
Preserve exact IDs, paths, commits, URLs, commands, errors, quoted decisions,
assumptions, unknowns and time-sensitive details where needed for continuation.
Transfer known material facts, not just pointers or instructions to reread them.
The handoff request itself is not a task decision. Keep preferences and proposals
distinct from requirements and accepted decisions.

Use `unknown` for missing information and `none known` when no instances are
known, such as no known blockers. Neither proves absence. Set `Status:
not_started` only when the conversation or an explicitly named or already
established task source establishes it; otherwise a missing status stays
`unknown`.

For file-based work, use the task working directory established by the
conversation or an explicitly named or already established canonical project
source. A task repository already verified during the work is sufficient; the
user need not name it again. If no task location is established, include
`Working directory: unknown`. Runtime CWD alone does not establish the task
location. Include temporary workspace or host state only when established as
task state.

Output secret-bearing facts only in redacted form: `NAME=[redacted]`.
Keep each established variable name. Redact every secret occurrence in quotes,
warnings and replacement instructions too; never show the original value
when explaining its removal.

For a tight output limit, remove repetition and unrelated history first, then
shorten explanations. Preserve authority, ownership, hazards, evidence limits
and the safe first step. An explicit lossless request preserves every in-scope
non-secret fact. If required content still cannot fit, publish the complete
unchanged fenced artifact through the shared complete-file route. Return its
absolute path, SHA-256 and an instruction to verify the hash and read the
entire file before continuing.

## Compose and check the prompt

Keep the template's four H2 sections: Receiver Instructions, Objective, State
and Resume Steps, with all three Resume Steps. Keep Receiver Instructions
intact except for translation and secret redaction. Use the requested language,
otherwise the conversation language; translate headings, labels and instructions
consistently. Preserve technical identifiers, literal markers such as `unknown`
and exact quotations except secret values.
Use one outer Markdown fence with at least four backticks and more backticks
than any run inside the prompt; match its opening and closing length, including
when saving the artifact to a file.
Include every Objective field. Under State, always preserve Status and the
required continuation facts, including relevant unknowns. Other template labels
are optional; omit empty or inapplicable categories. Name each source once beside
its facts and identify conversation facts as such. Repeat a fact only when a
hazard or first step needs it.

Choose Resume Step 1 in this priority order:

| Condition | First step |
| --- | --- |
| Goal unknown, or Acceptance unknown and next action depends on it | Ask before execution or recovering a running command. |
| Known blocker | Resolve the first blocker. |
| In-flight work | Recover its state. |
| Otherwise | Take the next safe action. |

Make the remaining steps concrete and end with an
observable completion criterion. Active or incompletely accepted work names its
decisive next check. For completed work with current evidence, the three steps
cover only checking current state, reconciling contradictions and confirming
no material mismatch. Do not invent more work or repeat a current check to fill
a step.

1. Compare the full prompt with captured facts and sources: required facts,
   exact identifiers, attribution, Objective fields, Receiver Instructions and
   first safe step. For lossless requests, check every in-scope non-secret fact.
2. Correct omissions and contradictions; remove placeholders, secrets, invented
   facts and tool details used only to prepare the snapshot.
3. Return exactly the fenced artifact without surrounding text, or the specified
   path, hash and complete reading instruction for file delivery.

Handoff owns the snapshot; preserve active sibling state in it.

This Skill works independently. Other Scoville Skills are optional. Use an
available, active sibling only for its applicable concern; do not install,
simulate or require an absent sibling. Honor explicit user exclusions.

Family owners, in suite order:

- `scoville-code`: engineering scope, implementation, risk, and validation.
- `scoville-plan`: durable Plans, Work Items, Decisions, and lifecycle state.
- `scoville-ui`: framework UI implementation and acceptance, including supported WordPress admin surfaces.
- `scoville-handoff`: active-work transfer.
- `scoville-project-context-cleanup`: requested project-rule and index wording, information quality and structure.

Reuse an already verified interpreter meeting this Skill's Python 3.11+
requirement. Otherwise check `py -3`
on Windows or `python3` elsewhere; try `python` if needed. Choose it locally,
without asking the user. Verify its version before the first helper operation.
Use that executable wherever examples say `python` or `<verified-python>`,
including Python commands after `--run --`.
Report a missing runtime only when no suitable installed interpreter is found.

For direct helper calls in PowerShell, quote the interpreter path and prefix it
with `&`. Run generated commands unchanged in the current tool shell; do not
replace their process or argument handling with a direct call.

## Runtime helpers

Use the bundled helpers for their operations. Read their invocation instructions,
not their source, unless diagnosing a failure.

Without an applicable limit, read complete UTF-8 directly; invent no budget.
With an applicable limit:

1. Use the smallest declared or explicitly selected limit of the command and
   every enclosing tool output. Read separately unless the complete combined output,
   including labels and metadata, is measured and fits; combined reads share
   that budget.
2. If the file may exceed that limit, use the verified Python interpreter and
   bundled reader:
   `<verified-python> -X utf8 "<skill-directory>/scripts/check_text_size.py" --file "<document>" --max-output-tokens <limit> --part 1`.
   It validates the complete UTF-8 file and budgets labels too.
   Python runs the full checker path `<skill-directory>/scripts/check_text_size.py`
   after `-X utf8`. The checker reads every document only through `--file`, including
   SKILL.md files and references of any Skill, assignments, and `.py` files read as
   text. Keep the verified launcher, checker path and quoting unchanged. Copy the
   last correct complete command: change only `--part` for the reported next part;
   for another document change only `--file` and reset `--part` to 1.
3. For multipart output, follow `part=N bytes=start:end/total next=M` with
   `--part M` through `last`,
   where end equals total. Read every unchanged part in order before dependent
   work. Use one limit for the whole sequence. If an applicable limit changes,
   restart at part 1 with the new smallest limit; never raise a binding limit
   to keep the old sequence.

Reader parts are already bounded. Execute the supplied reader command unchanged;
do not wrap it in `--run`, add `--publish-full`, or save its output.

A reader error leaves the read incomplete, even if its diagnostic cannot fit.
Correct a visible cause and restart at part 1. Do not repeat an unchanged failed
call or raise a binding limit. Otherwise report the unread document and stop
dependent work.
Do not alter or copy the input, truncate it or recover omitted text after an
oversized read.

To check a supplied expected SHA-256, use the same checker with
`--file "<artifact>" --sha256 --max-output-tokens <limit>` and compare its
`sha256` with the supplied value. A mismatch or error stops dependent work.
Then read the same unchanged file from `--part 1` through `last` with the same
limit. Hash verification is not reading; ordinary sources need no extra hash check.
Without suitable Python 3.11+, first read only the check_text_size reference below. Use
a native UTF-8 reader and ordered unchanged parts, measuring each complete
output including labels before display against `floor(limit * 4 / 5)` bytes.
With no limit, read it completely. Without a safe reader, stop dependent work.

| Condition | Required route |
| --- | --- |
| Suitable Python 3.11+ is available | Use the bundled helper; do not load manual references. |
| No suitable Python 3.11+ | Read only the matching optional reference below. |
| Missing script, missing dependency or helper error | Stop the affected operation; this never enables the manual route. |

| Helper | Optional no-Python reference |
| --- | --- |
| `scripts/check_text_size.py` | [check_text_size](references/fallbacks/check_text_size-fallback.md) |
