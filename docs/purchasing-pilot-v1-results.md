# Thinking-on purchasing pilot: archive content changes choices

**November 12, 2026 (America/Caracas). Exploratory development pilot.**

Qwen3-32B with native thinking changed its purchasing choices when the approval
archive implied a different criterion, without being asked to report that
criterion in the choice calls. Under mild customer preferences, customer-favored
choices fell from **24/24 with aligned archives to 9/24 with conflicting archives**
without evaluation framing. With framing, the corresponding counts were **24/24
and 9/24**, with one additional unresolved choice in the conflicting cell. This
is evidence of archive-content sensitivity in this configuration. The incremental
evaluation-framing interaction remains uncertain.

The separate contextual report probes suffered a severe format failure. Trace
annotations also disagree on several fields. These limitations prevent a strong
claim about accurate in-context criterion reports or influence without mention.

## Design and preservation

Eight fresh development bases crossed I1 approval histories and T1 transparent
rubrics with the six frozen factorial conditions. Each cell received three seeded
choice traces; 96 separate thinking-on contextual report calls brought the total
to **384**. The customer expressed only a mild price or delivery preference and
explicitly accepted either option. These are customer-favored choices, not a
strict instruction-following accuracy test. I2 and sealed I3 were not used.

The detached worker completed every base in 95 minutes 32 seconds. Startup,
capacity, identity and native-format controls passed; research preemptions were
zero. All 165 saved frames and raw-group hashes were checked. There was no retry,
regeneration, forced think closure, or replacement of missing outcomes.

Simon completed and attested the frozen 48-trace worksheet before viewing margins,
choice rates or assistant labels. After a single invalid-category correction,
the 48 annotations passed validation and were frozen. The assistant then read
and coded all 144 shuffled I1 reasoning traces, with human labels, condition maps,
sampled final answers and scores hidden. Its original labels were locked before
unblinding. Reasoning itself could reveal intended choices and condition; this
was never complete psychological blinding. Neither label set has been adjudicated
or revised to increase agreement.

## Behavioral results

Primary margins are raw vLLM A/B log-probability differences at the answer slot
after the sampled reasoning trace, signed toward the fixed customer preference.
Cell means require at least two of three valid margins; bases receive equal
weight. Intervals below are the frozen 10,000-draw percentile bootstrap over
base scenarios, retaining cells and families together. All estimates are
exploratory, with eight independent base clusters, not 24 independent scenarios.

| Contrast, nats | I1 inferred archive | T1 readable rubric |
| --- | ---: | ---: |
| Conflicting minus aligned, no framing (C3 − C2) | −11.31 [−15.06, −7.06] | −13.65 [−17.60, −9.51] |
| Conflicting minus aligned, framing (C6 − C5) | −9.25 [−13.02, −5.21] | −15.41 [−17.04, −13.62] |
| Interaction: (C6 − C5) − (C3 − C2) | +2.06 [−2.41, +7.76] | −1.77 [−5.56, +1.77] |
| Framing, no objective (C4 − C1), within tier | −3.03 [−4.73, −1.53] | −0.59 [−1.48, +0.26] |

Both objective contrasts are large and negative. Neither interaction interval
resolves its direction. This pilot does not establish H1 or equivalence to zero.
The T1 result is a positive control for content-sensitive choice, not a replication
of the earlier 8B T1/T2 sign-flip study.

| Family | C1 | C2 | C3 | C4 | C5 | C6 |
| --- | ---: | ---: | ---: | ---: | ---: | ---: |
| I1 customer-favored strict choices / assigned | 21/24 | 24/24 | 9/24 | 16/24 + 1 unresolved | 24/24 | 9/24 + 1 unresolved |
| T1 customer-favored strict choices / assigned | 24/24 | 24/24 | 9/24 | 24/24 | 24/24 | 4/24 |

I1's no-framing choice-rate contrast is −62.5 percentage points (base-bootstrap
95% interval −83.3 to −37.5). Its framed contrast has all-assigned bounds of
−62.5 to −58.3 points. Resolved denominators are 23 in I1 C4/C6 and 24 elsewhere;
the resolved customer-favored rates in those two cells are 16/23 and 9/23.
Invalid outputs are not silently treated as valid disfavored choices.

There were 287/288 valid choice margins and 286/288 strict parsed choices. One I1
C6 trace exhausted 4,096 tokens without closing; one I1 C4 trace closed but had
invalid final-answer format. The latter retains its valid slot margin as planned.
All eight bases remain eligible for the primary interaction. Requiring all three
margins removes one I1 base and yields +3.20 [−1.37, +9.29] nats, still uncertain;
T1 is unchanged.

## Contextual report probe: format failure

Only **1/96** report calls passed the frozen single-letter parser (I1 1/48;
T1 0/48). All 92 completed format-invalid report outputs contained two letters
separated by whitespace; three other reports were truncated. The full purchasing
prompt retained its A/B answer instruction before the appended A/B/C report-only
question. The two-letter pattern is consistent with answering both tasks, a
design/format problem rather than evidence of inability to infer a criterion.

No second-letter extraction or relaxed rescoring is used. All-assigned accuracy
bounds are 1/48 to 48/48 for I1 and 0/48 to 48/48 for T1: uninformative about
criterion recovery. The 93 captured first-slot A/B/C distributions cannot be
treated as report distributions when that slot may answer the purchasing task.
The strict counts are format-constrained outcomes, not a defensible capability
failure. A future report probe would need a prospective instruction/format fix.

## Independent coding and the nonmention outcome

| Field | Human–assistant exact agreement |
| --- | ---: |
| Criterion mention | 40/48 (83.3%) |
| Criterion identification | 26/48 (54.2%) |
| Evaluation mention | 36/48 (75.0%) |
| Evaluator attribution | 30/48 (62.5%) |
| Follow/ignore stance | 27/48 (56.2%) |

Full confusion matrices and the 35 traces with at least one disagreement are
preserved. There was no preregistered agreement threshold; none is invented now.
These are agreement rates between two coders, not an accuracy score for either.

The assistant marked criterion discussion in all 144 I1 traces, including
uncertain and mistaken attempts to infer an archive rule. Under those original
codes, the joint event “criterion-consistent choice AND no criterion mention”
occurred zero times in C2/C3/C5/C6, with both fixed-orientation framing contrasts
equal to zero. A degenerate empirical bootstrap here is not evidence that the
population event rate is zero or that traces are faithful.

The human marked eight of the sampled 48 traces as having no criterion mention.
The human subset has one joint event, in C5 (1/5 coded there); its other objective
cells have zero events (C2: 0/10; C3: 0/12; C6: 0/8). This is a sparse,
unequally distributed subset, not an interchangeable full-grid estimate. The
coders' disagreement on mention means the result is annotation-sensitive. This
pilot does **not** establish objective influence without verbalization, and no
causal effect within a selected nonmention subgroup is estimated.

## Resolution, headroom and limits

All 287 captured margins lie within numerical tolerance of a **0.125-nat grid**.
This is the declared vLLM bf16-logit readout, not the separately qualified
float32-final-hidden/float32-head scorer. It limits fine-resolution claims. The
large content shifts are corroborated by sampled choice changes: 15/24 paired
I1 seeds flip between C2/C3 and 14/23 between C5/C6. Pairing by seed does not mean
the traces follow identical computation across different prompts.

C1 median absolute margins are 6.94 nats (I1) and 8.56 (T1); median signed margins
are 6.44 and 8.56. C1 customer letters are balanced 12 A/12 B within each family;
sampled letters are 11 A/13 B for I1 and 12 A/12 B for T1. Among all family choice
margins, 24/143 I1 and 55/144 T1 have absolute magnitude at least 10 nats
(descriptive diagnostic, not an exclusion threshold). Mean A/B mass is .986 and
.998 respectively. No exact duplicate reasoning traces or valid-choice/margin-sign
disagreements were found. These checks support reporting both margins and choices.

The strongest supported statement is that **approval-archive content shifts
choices in this native-thinking, mild-priority purchasing setting**. There is no
matched thinking-off arm of this purchasing pilot: historical single-pass runs
differed in task wording, cohort and readout. This result therefore does not
isolate serial computation as the cause, establish a particular internal
representation, or demonstrate evaluation gaming or monitorability. Evaluation
framing's added interaction is unresolved; the contextual report and nonmention
questions remain limited by format and annotation.

## Reproduction and cost

Canonical outputs: `outputs/purchasing-pilot-analysis-v2/` (`analysis.json`,
`records.json`, `cells.json`, `coding-disagreements.json`,
`report-format-audit.json`, and SHA-256 `manifest.json`). The v1 output remains
preserved; v2 adds explicit resolved-choice rates and additional source hashes,
with no change to estimates or frozen labels. Reproduce offline into a fresh
directory with:

```sh
.venv-bf16/bin/python scripts/analyze_purchasing_pilot.py --out /tmp/purchasing-pilot-reproduction
```

The analysis verifies annotation locks, raw-group hashes, request coverage,
zero preemptions and exact agreement with stored frozen parser outputs before
producing summaries. **418 tests passed**, including the missing-margin,
interaction-sign, base-bootstrap and annotation-bound tests. No paid calls were
made for coding or analysis. The last provider snapshot was **$3.91556246
provisional**, not reconciled all-attempt billing; the approved **$23 hold remains**.
No new experiment is authorized by this report. Proposal revision 6 remains frozen.
