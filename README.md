# Scoville Handoff

Transfers the state. Leaves the session behind.

A weak handoff can look complete while making the next session reconstruct the
work:

- The goal survives, but the acceptance condition does not.
- Changed files survive, but their owners and staged state do not.
- A running command becomes "tests passed" even though no exit code was seen.
- Publication, destructive work, or a commit appears authorized because the
  missing boundary was never transferred.

Scoville Handoff is an Agent Skill for moving active work to another agent or
session as one compact, copy-ready continuation prompt. It preserves the facts
that determine what the receiver may do, what must be verified, and which
action is safe to take first. It activates only for an explicit transfer
request; a summary, wrap-up, or shrinking context is not a handoff.

## Why "Scoville Handoff"?

The Scoville family is named for useful signal that remains detectable after
dilution. A handoff compresses a long working session, but its operational
signal must survive: objective, acceptance, canonical sources, ownership,
authority, current evidence, hazards, and the next safe action. Conversation
history is disposable. Those facts are not.

## Install

Use an agent that supports the Agent Skills format: a `SKILL.md` instruction
file with its name and description at the top. Terra 5.6 Medium or a comparably
capable executor such as Opus 4.8 is the minimum supported capability level.

Usually, let the agent install the Skill. Send it this prompt:

```text
Install this Agent Skill from GitHub and make it available for my work:
https://github.com/benjaminstelzer/scoville-handoff/tree/main/scoville-handoff
Use Terra 5.6 Medium or a comparably capable executor such as Opus 4.8; this is the minimum supported capability level for this Skill.
```

Add "for all my projects" or "only for this project" when the installation
scope matters. The agent should install the directory under the unchanged name
`scoville-handoff` and refresh its Skill list. If manual copying is necessary,
the installed path must end in:

```text
<skills-dir>/scoville-handoff/SKILL.md
```

For Claude Code, `<skills-dir>` is `~/.claude/skills/` for all projects or
`.claude/skills/` inside a repository for one project. Other hosts use their
own supported Skills directory. Refresh the host's Skill list after copying.

Ask for `Scoville Handoff`, a `compact handoff`, `context handoff`, `session
handoff`, or an `Übergabe an neue Session`. Explicit `$scoville-handoff`
invocation works where the host supports named Skill invocation. The former
`$compact-handoff` identifier is retired; its natural-language phrases remain
valid.

**What it costs.** Compatible hosts expose compact discovery metadata before
loading the full Skill instructions. Scoville Handoff has one 1,086-token core
and no conditional references. Compared with the last released Compact Handoff
`v1.0.0`, the loaded instructions fell from 1,689 to 1,086 tokens (-35.70%).
Activating any Skill still adds prompt context and can use materially more
provider tokens than working without one. That overhead buys a safer transfer
of authority, ownership, dirty state, evidence, in-flight work, secrets, and
the first recovery action. Use Handoff for long, interrupted, risky, or
reviewable work where accurate continuation matters. Leave it inactive for a
small, fast vibe-coding task when no real session transfer is needed and token
use matters more. Provider usage also depends on the host and conversation.
See [benchmark evidence](docs/benchmark-evidence.md) for scope and limits.

## What it enforces

- **Explicit transfer only.** A direct request to move work creates a handoff.
  Summaries, recaps, wrap-ups, low context, and session endings do not.
- **One fixed receiver contract.** Every positive result contains Receiver
  Instructions, Objective, State, and Resume Steps inside one copy-ready
  Markdown artifact.
- **Facts instead of pointers.** Named sources are read once. Their material
  facts and paths enter the handoff; the receiver is not told to discover the
  missing state later.
- **Authority and ownership survive.** Commit, publication, destructive-action,
  external-effect, file-owner, and dirty-tree boundaries remain explicit.
- **Unknown stays unknown.** An observed running process never becomes a
  success claim. Missing state is marked `unknown` or `none known`, not guessed.
- **Secrets do not travel.** A needed variable name may remain, but its value is
  redacted.
- **The receiver can act.** Resume Step 1 resolves the first blocker, recovers
  in-flight work, or performs the next safe action. The final step names an
  observable completion criterion.
- **No task progress during transfer.** Handoff may read named task sources and
  inspect version control read-only. It does not edit, publish, probe, or run
  the task it is transferring.

The full rules live in [SKILL.md](scoville-handoff/SKILL.md).

## Use with the Scoville family

Handoff works independently. Companion Skills remain optional and own separate
concerns.

Use [Scoville Plan](https://github.com/benjaminstelzer/scoville-plan) for
durable repository Plans, Work Items, Decisions, and lifecycle state. Handoff
does not replace or modify those records; it transfers the current snapshot
and tells the receiver to verify the canonical owner.

Use [Scoville Code Anti-AI-Slop](https://github.com/benjaminstelzer/scoville-code-anti-ai-slop)
for engineering scope, implementation integrity, risk, and validation. Use
[Scoville UI Anti-AI-Slop](https://github.com/benjaminstelzer/scoville-ui-anti-ai-slop)
for interface hierarchy, framework alignment, accessibility, responsiveness,
and rendered evidence. Use
[Scoville Scribe Anti-AI-Slop](https://github.com/benjaminstelzer/scoville-scribe-anti-ai-slop)
for reader-facing meaning, terminology, localization, and source fidelity.
Handoff preserves their relevant state without requiring or simulating them.

## Design

The Skill uses a compact transfer machine:

1. `READ` loads each named source exactly once.
2. `CAPTURE` records every non-secret continuation fact in an in-memory ledger.
3. `RENDER` maps that ledger into the four fixed sections.
4. `CHECK` compares the artifact with the ledger without rereading sources.
5. `SEND` returns only the fenced handoff.

Optional facts are compact labeled bullets under `State`, not a forest of empty
sections. Empty or not-started work still produces the full four-section
artifact because the receiver must know that the absence of progress is real.

The Skill does not replace project instructions, version control, durable
planning records, human authorization, or current-state verification. A
handoff is a snapshot, not a lease on reality.

## Sources and inspirations

- The previous Compact Handoff release for explicit activation, snapshot
  freshness, secret redaction, and copy-ready transfer.
- [Microsoft SkillOpt](https://github.com/microsoft/SkillOpt) for
  validation-driven Skill optimization.
- [SkillReducer](https://arxiv.org/abs/2603.29919v2) for semantic-unit
  classification, redundancy removal, and progressive-disclosure principles.
- [The Agent Skills specification](https://agentskills.io/specification) for
  installable Skill structure and metadata conventions.
- [OWASP LLM06: Excessive Agency](https://genai.owasp.org/llmrisk/llm062025-excessive-agency/)
  for keeping consequential authority explicit across agent boundaries.

## Repository contents

The installable `scoville-handoff/` directory contains the core Skill and
display metadata. [Evaluation cases](tests/evaluation-cases.json),
[benchmark evidence](docs/benchmark-evidence.md), and the
[optimization-run ledger](docs/optimization-runs.md) remain outside the
installable package. The README, changelog, project records, and MIT license
are documentation and are not loaded as Skill instructions. The Skill installs
no executable software and performs no runtime network fetch.

## Status

[Microsoft SkillOpt](https://github.com/microsoft/SkillOpt) was extended to
prioritize reliability before compression and combined with SkillReducer-style
reduction. Across the five Scoville Skills, development recorded **1,019
optimization and evaluation runs**. Scoville Handoff accounts for **222 runs
and 620 benchmark case executions**, passed **3/3 new sealed qualification
cases**, and uses **35.70% fewer loaded instruction tokens than Compact Handoff
v1.0.0**. Minimum executor: Terra 5.6 Medium or comparable, such as Opus 4.8. See
[benchmark evidence](docs/benchmark-evidence.md).

## License

MIT - see [LICENSE](LICENSE).
