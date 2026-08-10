---
format_version: 1
id: ADR-0002
status: accepted
created: 2026-08-10
accepted: 2026-08-10
scope: project/compatibility
---

# Retire the Compact Handoff runtime alias

## Decision

Preserve established natural-language requests such as `compact handoff` and `session handoff`, but retire the installed `compact-handoff` directory and explicit `$compact-handoff` identifier after the `scoville-handoff` replacement passes local validation. Do not install two Skills with overlapping activation contracts.

## Problem

The full rename changes an explicit Skill identifier that existing prompts may use. Keeping both packages would preserve that identifier but expose duplicate discovery metadata and overlapping activation rules, weakening the goal of one recognizable Scoville sibling.

## Drivers

- Avoid ambiguous activation and duplicate Skill instructions.
- Preserve the natural-language requests users are most likely to reuse.
- Keep folder name, frontmatter name, and displayed identity consistent.
- Make removal recoverable through a staged local backup and byte comparison.

## Considered alternatives

- Install both complete Skills: preserves the explicit alias but creates duplicate ownership and divergent-update risk.
- Keep `compact-handoff` as the runtime name and change only the display name: avoids migration but leaves the Skill outside the canonical Scoville namespace.
- Remove both the old identifier and old phrases: yields the smallest contract but breaks avoidable natural-language compatibility.

## Consequences

Prompts that explicitly invoke `$compact-handoff` must change to `$scoville-handoff`. Existing natural-language handoff requests remain valid. Local migration must stage and validate the replacement before removing the old installed directory, and no deletion may occur outside the explicitly scoped Codex and Claude Skill locations.

## Confirmation

In isolated Codex and Claude discovery checks, exactly one Handoff Skill appears under the Scoville identity; legacy natural-language requests still activate it; the old explicit identifier is absent; and the installed bytes match the validated candidate.

## Revisit when

Codex, Claude Code, or the Agent Skills specification adds a portable alias mechanism that preserves one canonical package without duplicate discovery.
