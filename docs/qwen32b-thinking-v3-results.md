# Qwen3-32B mode comparison — completed strict-parser diagnostic

On the fixed 36-history I1 cohort, the same bf16 weights and vLLM configuration
recovered the archive criterion on **32/36 thinking-on reports (88.9%)**, versus
**11/36 thinking-off reports (30.6%)**. Every report in both arms finished normally
and passed the frozen strict parser. No truncation, missing item, extraction repair,
accuracy-based stop or post-outcome retry. These are exploratory report-task results,
outside every qualified choice-scoring/manipulation gate.

| Cohort | Thinking on | Thinking off |
| --- | ---: | ---: |
| I1 criterion reports | 32/36 | 11/36 |
| Minimal explicit-criterion controls | 6/6 | 6/6 |
| All assigned outputs parsed | 42/42 | 42/42 |

Paired I1 outcomes: 23 correct only with thinking on, two correct only off, nine
correct in both, two incorrect in both. The descriptive paired difference is
**+58.3 percentage points**, with a scenario-cluster bootstrap percentile interval
of **[+38.9, +77.8] points**. Resample the 36 base identities jointly across modes;
controls remain separate. The estimation implementation uses the project's existing
20,000-replicate / seed 2026110503 convention. It was implemented post-run for this
preplanned uncertainty estimate, not used for any selection or gate. No p-values
or confirmatory tests; uncertainty is conditional on this fixed balanced cohort,
one sample per item/mode, one pretrained checkpoint and this inference configuration.

## Semantic confusion, all assigned I1 reports

Rows are true archive criterion, columns are predicted criterion. Twelve histories
per row; labels and positions were counterbalanced before generation.

| Thinking on | Price | Time | No consistent criterion |
| --- | ---: | ---: | ---: |
| Price | 10 | 1 | 1 |
| Time | 0 | 10 | 2 |
| No consistent criterion | 0 | 0 | 12 |

| Thinking off | Price | Time | No consistent criterion |
| --- | ---: | ---: | ---: |
| Price | 6 | 3 | 3 |
| Time | 7 | 5 | 0 |
| No consistent criterion | 6 | 6 | 0 |

All four on-mode errors and all 25 off-mode errors remain in the machine-readable
estimation report. Six explicit controls per arm are minimal sanity checks, not a
replacement for the earlier full format qualification or a passing manipulation gate.

## What the comparison establishes and leaves open

These 32B weights can recover I1 archive criteria in the native thinking-on mode on
this cohort. A blanket inability to perform this report task is therefore too broad.
The earlier first-pass negative results remain valid in their stated configurations.
The 8B thinking result remains censored at 1,024 tokens; this run does not settle 8B
with an adequate allowance.

Mode changes both the native assistant prefix and the availability of serial
generation. This result does not isolate computation length from mode/template
instructions, show that criterion information was absent in off-mode activations,
or establish what an activation monitor would need to read. It tests reports about
the archive, not whether purchasing choices follow the recovered criterion or whether
the model infers a current evaluator's actual goals. No purchasing behavior was
generated here. Report-trained organism transfer and internal causal dissociation
remain separate prospective studies.

Both new arms use this same frozen generation engine and sampler. Historical
PyTorch/bf16-backbone/FP32-head scores are separate references, not the off-arm
control. There is no scorer/certificate promotion or layer/hyperparameter selection.
I2 was prospectively excluded; I3/test data were not consumed. Prior negative and
frontier-validity reports remain unchanged.

## Completion and infrastructure

All eight early I1 on-mode items closed thinking and reached EOS, so the fixed
completion-only futility gate continued. No accuracy was parsed until the terminal
receipt existed. All 21 frozen groups finished with **zero native preemptions**.
Reported KV capacity was 56,128 tokens at utilization 0.95. One first-try matched
A100-SXM4-80GB allocation, driver 610.57.04 / CUDA 13.0; no hardware rerolls.

The native prefix/EOS audit, raw generated token IDs and durable per-frame hash
receipts are retained. There were **72,436 generated tokens** total. I1 on-mode
lengths: minimum 913, median 1,886, maximum 3,511; every off-mode output used two
tokens (letter plus EOS). Controls on-mode used 153–289 tokens. The 8,192-token cap
was never reached. Worker duration was **2,429.08 seconds (40.48 minutes)**, which
excludes some provider phases and is not an all-in bill.

The live CPU streaming probe passed before either research launch. It caught one
local SDK-registration issue before remote submission; the archived repair removed
the unsupported generator retries argument. This research run had no transport
failure, worker retry or source/configuration change. Its app is stopped with zero
tasks; only the independent transparent screen continues.

The original **$24 all-attempt hold remains** pending final provider-hour charges,
including startup, image overlay, CPU/RAM/GPU, transport and any adjustments. Do not
replace it with worker-time estimates. Raw evidence: `outputs/qwen32b-thinking-run-v3/`;
strict scoring: `scripts/analyze_thinking_v3.py`; descriptive paired uncertainty and
semantic confusion: `scripts/estimate_thinking_v3.py`. Frozen parser source precedes
launch and is checked against the packet before any report is parsed.
