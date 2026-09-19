---
name: scoville-handoff
description: Transfer active work to another agent or session as one compact, factual, copy-ready continuation prompt with fixed Receiver Instructions, Objective, State, and Resume Steps. Use only when the user explicitly asks for Scoville Handoff, a compact/context/session handoff, a handoff to a new session, "Übergabe an neue Session", or an equivalent transfer. Preserve objective, decisions, state, ownership, evidence, blockers, hazards, and next safe action. Do not use for summarizing, shortening, wrapping up, ordinary context reduction, low context, or session ending. Read only named task sources and optional version control; run no task or dummy command.
compatibility: "Any Agent Skills host that can read the named task sources. Optional read-only version-control inspection (git). No scripts, no network, no subagents. Developed for Codex and Claude Code; other hosts untested."
---

# Scoville Handoff

Create the fixed portable artifact only for an explicit transfer.

## Dispatch

- `yes`: explicit agent/session transfer; empty, completed, or not-started work
  stays `yes`.
- `no`: no receiver transfer. Perform the task; emit no handoff.
- `ambiguous`: future reuse without a receiver. Ask one question; read nothing
  and emit no handoff.

## Transfer machine

For `yes`: `READ -> CAPTURE -> RENDER -> CHECK -> SEND`.

1. **READ:** Read only named sources and optional read-only version control.
   Mark each result complete, partial, or failed under its exact source path.
   Finish a truncated read through the missing range or continuation cursor.
   Retry a failed range once only for a plausibly transient error. Stop recovery
   on no progress or repeated failure. Preserve partial facts and name unread
   ranges. Explicit user read limits take precedence. Record recovery and gaps
   beside the affected source. No unrelated read, stat, list, probe, edit,
   external effect, dummy command, or task command is authorized.
2. **CAPTURE:** Ledger non-secret continuation facts from each usable result,
   never calling a partial source wholly unavailable. The mandatory set is the
   goal, deliverable, acceptance, scope and authority, canonical owners,
   user-owned changes, accepted decisions, active work and running handles,
   observed evidence and its limits, blockers, hazards, and next safe action.
   Keep supporting IDs, paths, commits, URLs, commands, errors, quoted decisions,
   assumptions, unknowns, and time-sensitive details exactly where needed to
   preserve that set. Omit unrelated history and repetition, not required facts.
   Never substitute a source name or reread instruction for known material facts.
   The handoff request is
   not itself a decision. Use `unknown` or `none known` instead of inference.
   Omit secret values; retain a needed variable name and mark its value
   redacted. Runtime CWD, temporary workspace, and host state are not task facts
   unless the user or a named source supplies them.
   Under a tight output limit, remove repetition and irrelevant history first,
   then shorten explanation. Never drop authority, ownership, hazards, evidence
   limits, or the safe first step. If the mandatory set still cannot fit, report
   the size conflict and request a larger limit instead of claiming completeness.
   An explicit lossless request preserves every in-scope non-secret fact, not
   merely the mandatory set. Conflicting source revisions or material unread
   ranges remain explicit blockers for receiver verification.
3. **RENDER:** Copy [the continuation template](assets/continuation-prompt.md) with all H2s and fixed Receiver bullets, then replace its placeholders with captured facts. Under
   `State`, label every applicable fact; name each source once beside its facts;
   repeat a fact only for a hazard or first step; omit only empty labels. Empty
   or not-started work still renders fully with `Status: not_started` and
   required `none known` values. Step 1 resolves the first blocker, else
   recovers in-flight work, else takes the next safe action. Keep the template's
   Markdown fence so the returned artifact stays copy-ready.

4. **CHECK:** Compare with the ledger: include the complete mandatory set and
   its exact identifiers and source attribution, every required Objective field,
   fixed Receiver bullet, and first safe step. For a lossless request, check all
   in-scope non-secret facts instead. Steps
   are concrete and end in an observable completion criterion; no placeholder,
   secret, invention, or capture-only tool detail remains. Failure returns to CAPTURE.
5. **SEND:** Return exactly the fenced artifact, with nothing outside it. If an
   explicit size limit prevents safe transfer, return only the concise size
   conflict and requested limit change instead of an incomplete artifact.

Handoff owns the snapshot.

Discovering a sibling does not mean it is installed, active, applicable, or required. If a sibling is absent or inactive, ignore it. Do not require, install, simulate, or reimplement it. If it is active and applicable, it owns only its concern. This Skill continues. Opt-out is local.

Family owners, in suite order:

- `scoville-brainstorm`: deliberate divergence before selection.
- `scoville-research`: source-backed research and synthesis.
- `scoville-code-anti-ai-slop`: engineering scope, implementation, risk, and validation.
- `scoville-design-anti-ai-slop`: visual definition, art direction, critique, and repair.
- `scoville-ui-anti-ai-slop`: framework UI implementation, accessibility mechanics, and rendered proof.
- `scoville-scribe-anti-ai-slop`: wording, terminology, meaning, and source fidelity.
- `scoville-plan`: durable Plans, Work Items, Decisions, and lifecycle state.
- `scoville-handoff`: active-work transfer.

Preserve active sibling state in the snapshot.
