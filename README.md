# Scoville Handoff

Scoville Handoff turns the current task into one copy-ready continuation
prompt: the goal, decisions, unfinished work, blockers and next action.
Another session can pick up the work without asking you to explain it all again.

Scoville measures chili heat. Handoff keeps the useful context from being
diluted between conversations. The next agent already has enough imagination.

## How it works

- It starts when you ask for a handoff. A summary, a full context window or
  the end of a session isn't a request.
- It uses what the conversation already established and reads only the
  sources named there. Nothing new gets researched.
- Writing the handoff leaves the task alone: no edits, builds or tests. The
  prompt shows the state at the moment you asked.
- Decisions, permissions and blockers carry over as they were. What nobody
  knows is written as `unknown`, not guessed. Secrets become `[redacted]`.
- The prompt ends with one to three next steps. The receiving agent checks
  the current state before it acts and doesn't take the handoff as new
  permission.

## How to use

```text
Use Scoville Handoff to transfer this active task to a new session. Include the current repository state and verified evidence.
```

```text
Create a compact handoff for another agent. Preserve the objective, decisions, changed files, blockers and next action. Do not continue the work.
```

The prompt comes in the language you ask for, otherwise in the language of the
conversation. Paste it into the new session.

## Install

Works in Codex and Claude Code. It needs Python 3.11+ for its bundled helper, no
network and no subagents.

Use `gpt-6.2-sol` or Claude Opus 5.5 at medium reasoning effort or higher. Below
that, steps get skipped more often.

Ask your agent host:

```text
Install this Skill for all my projects from this exact package directory:
https://github.com/benjaminstelzer/scoville-handoff/tree/main/scoville-handoff
Preserve personal settings and unrelated Skills. Report the installed location
and whether the host discovers the Skill.
```

The host needs write access to its Skills directory. The
[Codex](https://learn.chatgpt.com/docs/build-skills) and
[Claude Code](https://code.claude.com/docs/en/skills) Skills guides say where
that is. This Skill works on its own. The other Scoville Skills are in the
[Scoville Suite](https://github.com/benjaminstelzer/scoville-suite).

## Background

Handoff grew out of real transfers that lost blockers, decisions and the
question of who owned the unfinished changes.

On one transfer task with 16 check points, every run with Handoff met them
all - `gpt-6.1-sol` in 4 of 4 runs, Claude Opus 5.5 in 3 of 3 - and no run
without it did.

The [full instructions](https://github.com/benjaminstelzer/scoville-handoff/blob/main/scoville-handoff/SKILL.md) are what the agent reads.
Sources: Compact Handoff `v1.0.0`,
[Microsoft SkillOpt](https://github.com/microsoft/SkillOpt),
[SkillReducer](https://arxiv.org/abs/2603.29919v2), the
[Agent Skills specification](https://agentskills.io/specification) and
[OWASP LLM06](https://genai.owasp.org/llmrisk/llm062025-excessive-agency/).

## License

MIT. See [LICENSE](LICENSE).
