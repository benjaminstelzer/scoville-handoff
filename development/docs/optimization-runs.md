# Scoville Handoff optimization runs

## Totals

The preserved local optimization history through 2026-08-10 contains:

- 222 optimization and evaluation run directories;
- 221 completed evaluator runs;
- 620 benchmark case executions;
- one Microsoft SkillOpt run with 12 model calls: nine target rollouts and
  three analyst calls.

A run is one top-level model-backed evaluator or optimizer invocation preserved
under SkillOpt Studio `runs/`. A case execution is one stored evaluator result;
repetitions and comparison arms count separately. Schema-only preflight
failures before any model call are not runs.

## Phase ledger

| Phase | Run directories | Case executions | Purpose |
| --- | ---: | ---: | --- |
| Compact Handoff baselines and early pilots | 14 | 69 | Freeze released behavior and expose initial harness limits. |
| Scoville identity, reliability, state-machine, and reduction iterations | 198 | 515 | Test activation, source reads, dirty state, ownership, authorization, secrets, Plan composition, in-flight work, and compact output variants. |
| Final repeated open candidate | 6 | 27 | Run six Train cases and three Validation cases three times each. |
| Microsoft SkillOpt | 1 | 0 evaluator rows | Evaluate nine rollouts and three Sol analyst decisions without Test access. |
| Discarded sealed comparison arms | 2 | 6 | Preserve the wrong-comparator and scorer-contract diagnostic without using it for qualification. |
| Final sealed candidate qualification | 1 | 3 | Execute three new opaque cases once after the benchmark adapter was corrected. |
| **Total** | **222** | **620** | |

The SkillOpt row has no generic evaluator rows, so its nine rollouts are not
added again to the 620 case-execution total.

## Final candidate result

The final candidate passed 3/3 new sealed qualification cases in one fresh
Candidate-only run. The repeated open development split produced 18/18 Train
and 8/9 Validation semantic outcomes; the sole miss was a one-off
family-ownership collapse. Open diagnostics are not folded into the sealed
qualification score. Fable independently reviewed the three final outputs and
returned 3/3. Raw test-contract failures and their narrow adjudication are
documented in [benchmark evidence](benchmark-evidence.md).
