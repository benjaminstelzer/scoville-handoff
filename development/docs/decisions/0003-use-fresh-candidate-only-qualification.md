---
format_version: 1
id: ADR-0003
status: accepted
created: 2026-08-10
accepted: 2026-08-10
scope: project/qualification
---

# Use a fresh candidate-only sealed qualification

## Decision

Qualify the frozen Scoville Handoff candidate with one new opaque three-case Candidate-only Test after discarding the exposed wrong-comparator run. Keep repeated open results and the released-version token comparison as supporting evidence rather than combining them into the qualification score.

## Problem

The first sealed run bound Compact Handoff v1.0.0 instead of a preserved reliability-matched uncompressed control. Its generic scorer also required JSON from Markdown output and contradicted the host's mandatory Skill read. Once the cases were opened for diagnosis they could not be reused. No clearly qualified pre-reduction control remained from which to make the planned paired claim.

## Drivers

- Preserve the one-shot and no-reuse boundary after Test exposure.
- Require direct evidence that the final frozen candidate works on unseen tasks.
- Avoid inventing or reconstructing a reliability-matched control after the fact.
- Keep direct token measurement against the last released version factual and separate.
- Finish with the smallest new evaluation that can still disprove candidate reliability.

## Considered alternatives

- Accept the first candidate output audit as qualification: inexpensive but it would override the frozen gate after observing the cases.
- Mint another paired Test with a reconstructed control: preserves pairing in name but lacks a proven control and creates false precision.
- Mint a fresh Candidate-only Test: cannot attribute a failure to compression but can validly qualify a 3/3 candidate without reusing exposed cases.

## Consequences

The final public qualification score is the new sealed Candidate-only 3/3 result. The repeated open split remains diagnostic and its one semantic miss remains visible in detailed evidence. The discarded comparison stays preserved but contributes neither pass nor failure to the final Skill score. Token savings use deterministic `o200k_base` counts against Compact Handoff v1.0.0 rather than a paired runtime estimate.

## Confirmation

Verify that a fresh author created three unseen schema-valid cases without reading the Skill or prior suites; a separate fresh Terra 5.6 Medium agent executed them once against the bound candidate hash; all outputs preserve their task and safety semantics; no retry or reuse occurred; and the raw scorer defects remain separately documented.

## Revisit when

A preserved reliability-matched uncompressed control and a scorer that separates host overhead from task behavior are available before a new candidate is generated.
