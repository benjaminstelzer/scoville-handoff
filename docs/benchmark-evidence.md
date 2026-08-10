# Scoville Handoff benchmark evidence

## Final qualification

The local release candidate is the exact `scoville-handoff/SKILL.md` with
SHA-256
`D9D92F1131C99CE72654FCA7BB57E9E0C2D9497947DFB07DB00FE1360E9490C9`,
qualified on 2026-08-10. Optimization analysis used `gpt-5.6-sol` at `xhigh`;
execution used `gpt-5.6-terra` at `medium`. Network access and prediction reuse
were disabled.

The qualifying Test contained three new opaque cases and ran once through one
fresh agent after the candidate hash was fixed. The candidate passed 3/3 by
direct semantic review and an independent Fable 5 High audit. No case was
retried, reminted, or reused.

| Qualification case | Result |
| --- | ---: |
| Dirty release ownership, external state, and redacted secret | Pass |
| Blocked not-started migration and integrity gate | Pass |
| Negative non-transfer copy edit | Pass |
| **Sealed qualification** | **3/3** |

The repeated open development split remained useful diagnostic evidence:
Train preserved the task outcome in 18/18 observations; Validation did so in
8/9. The single miss collapsed several explicitly named sibling owners into a
generic family state. The other two repetitions preserved those owners. Open
development results are not aggregated into the sealed qualification score.

The qualifying Test's raw generic Studio score was 0/3. That raw result is
retained but is not the Skill score. In all three rows, the command allow-list
excluded the executor's quoted PowerShell prefix while every required command,
forbidden-command check, read phase, exact-once read, and shell budget passed.
One positive row required the redacted secret in one exact punctuation form,
although the output preserved the variable name and clearly marked its value
redacted. The negative row required an ASCII apostrophe while the correct
sentence used a typographic apostrophe. Direct inspection and Fable's audit
found no missing task fact, safety boundary, source boundary, authority rule,
recovery action, or activation decision.

An earlier sealed attempt is retained as diagnostic evidence but does not
qualify the Skill. It used the released version instead of a reliability-matched
comparison arm and contained mutually contradictory generic scoring rules. The
cases were exposed during diagnosis and were never reused.

## SkillOpt and reduction

The Microsoft SkillOpt checkout was clean at commit
`ba820b500f9da96685cf2780c7dc85ed4eb6563e`. The run
`scoville-handoff-skillopt-reducer-v1` used the six-case Train split, a
three-case selection split, Sol 5.6 xhigh analysis, and Terra 5.6 Medium
execution. It made 12 model calls: nine target rollouts and three analyst calls.
The optimizer selected the supplied four-section Skill without applying a
weaker patch. Fable's subsequent output audit added canonical-source and
observable-completion hardening; the affected open and sealed behavior was
rerun against the final hash.

SkillReducer-style reduction was applied before the SkillOpt run: semantic
units were classified by safety and task impact, duplicated prose and empty
conditional sections were removed, and the remaining rules were arranged as a
small state machine. Reliability requirements were restored selectively when a
failure exposed a concrete missing boundary.

## Token effect

Token counts use `o200k_base` over the exact UTF-8 `SKILL.md` files.

| Package | Bytes | Loaded Skill tokens |
| --- | ---: | ---: |
| Compact Handoff v1.0.0 | 8,258 | 1,689 |
| Scoville Handoff candidate | 4,968 | 1,086 |
| Change | -3,290 | -603 (-35.70%) |

These are literal loaded instruction tokens, not provider totals. Provider
usage also includes host instructions, conversation state, tool traces,
generation, and cache behavior.

## Reproducibility bindings

- Candidate Skill SHA-256:
  `D9D92F1131C99CE72654FCA7BB57E9E0C2D9497947DFB07DB00FE1360E9490C9`
- Released control Skill SHA-256:
  `AE119B7966332EC99B90AC072EA1ECD0B342E69274674E4840BC95DAB7E7D3B3`
- Sealed benchmark lock SHA-256:
  `213A4D3516E40FAD401B554D2F1103743CE5FB62B5C0C6C90B415B957DAA38B2`
- Arm binding SHA-256:
  `29A1467E8348F1FACDDC0CED7597F44BC57AA366EB67AC06E50AAACF719748BE`
- Candidate holdout summary SHA-256:
  `150389545E77FFD0AED97D21843CF2FA46335978BE7DA071ED323C52A774764F`
- SkillOpt revision:
  `ba820b500f9da96685cf2780c7dc85ed4eb6563e`

The complete prompts, scorers, traces, provider usage, outputs, and preserved
raw results remain in the local SkillOpt Studio workspace under
`benchmarks/scoville-handoff*` and `runs/scoville-handoff*`.

## Overall optimization history

The local history contains 222 run directories: 221 completed evaluator runs
and one SkillOpt optimization run. The evaluator runs contain 620 case
executions. See [optimization runs](optimization-runs.md) for the phase counts
and definitions.

## Interpretation limits

The result shows high reliability and a smaller loaded instruction payload on
these frozen cases with Terra 5.6 Medium. It does not prove deterministic
behavior, universal correctness, equivalent behavior on weaker executors, or
lower total provider usage than working without a Skill.
