# Compact Handoff

A small Agent Skill—a reusable instruction file for coding agents—for handing
unfinished work to another agent or session without dragging the whole
conversation along.

It produces one copy-ready English prompt. That prompt records the goal, current
state, decisions, evidence, blockers, and next safe action. It also tells the
receiving agent to verify the summary before continuing: the handoff describes
what was true when it was written, while the files may have changed since then.

## Install

Use an agent that supports the Agent Skills format: a `SKILL.md` instruction
file with its name and description at the top.

Usually, the simplest option is to send your agent this prompt:

```text
Install this Agent Skill from GitHub and make it available for my work:
https://github.com/benjaminstelzer/compact-handoff/tree/main/compact-handoff
```

Add `for all my projects` or `only for this project` to choose where the skill
is available. The agent should use its supported skills directory, keep the
installed folder name `compact-handoff`, and refresh its skill list.

For a manual installation, copy the repository's `compact-handoff/` directory
so the final path is:

```text
<skills-dir>/compact-handoff/SKILL.md
```

Skill directories vary between agents. Check your agent's documentation if it cannot choose the location itself.

## Use

Ask for a `compact handoff`, `context handoff`, `session handoff`, or `Übergabe
an neue Session`. The skill returns one Markdown code block and nothing else;
it does not get to wish the next agent luck.

**It only runs when you ask.** The skill never produces a handoff on its own.
Running low on conversation space, finishing a task, or approaching the end of
a session are not requests. Neither is asking for a shorter answer or a
summary. If the skill activates without an explicit handoff request, it says so
in one sentence and gets back to work.

Asking in your own words is enough. "Hand this over to a new session" triggers
the skill exactly as `$compact-handoff` does. The line it will not cross is
producing a handoff nobody asked for.

Beyond reading the conversation, it checks the version-control system, such as
Git, for three facts:

- the current line of development, called the branch;
- the latest version recorded by Git, called the commit;
- any file changes that have not yet been recorded in a commit.

This check cannot change files. Anything the skill cannot observe, including
timestamps, is marked `unknown` rather than guessed.

**What it costs.** `SKILL.md` is about 1,300 words, including a roughly
300-word prompt template. The agent reads this text as part of the conversation
context when the skill runs. The exact token cost depends on the agent.

It complements workflow guardrails such as
[Scoville](https://github.com/benjaminstelzer/scoville-anti-ai-coding-slop).
Scoville controls the brief notes an agent keeps while the same task continues;
Compact Handoff creates the separate copy-and-paste prompt used to move that
task to another agent or session.

## License

MIT. See [LICENSE](LICENSE).
