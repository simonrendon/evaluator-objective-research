# Criterion recovery across five Qwen3 sizes

**Final exploratory bridge report · November 9, 2026 · Simon Rendon**

The bridge adds four measured sizes to the existing Qwen3-32B native-mode
comparison. Thinking-on strict report accuracy rises across the measured sizes,
but the smaller points mix criterion recovery with format compliance and, at
1.7B/4B, truncation. The clean paired comparisons are **8B: 26/36 on versus 13/36
off**, and **32B: 32/36 on versus 11/36 off**. Immediate candidate-label scores
remain weak at the four newly measured sizes. These are development-cohort
observations, not confirmatory evidence of a causal size effect or computational
necessity.

![Five-size native-mode report comparison](proposals/figures/qwen3-mode-response-sweep-v1.png)

*All points use 36 paired I1 histories and one sampled response per mode/item.
Hollow triangles retain all assigned items, including invalid or capped outputs;
they do not isolate inference accuracy. Lines connect only fully parsed points.
32B is the earlier matched-cohort run. Sol's separate 432-prompt reasoning-enabled
check is an external readability reference, not another point on the Qwen curve.*

## Results under the frozen parser

| Size | Off correct / 36 | On correct / 36 | Off parsed / 36 | On parsed / 36 | Explicit controls, off / on |
| --- | ---: | ---: | ---: | ---: | --- |
| 0.6B | 0 (0.0%) | 9 (25.0%) | 1 | 25 | 1/6 · 6/6 |
| 1.7B | 5 (13.9%) | 13 (36.1%) | 24 | 31 | 6/6 · 6/6 |
| 4B | 11 (30.6%) | 20 (55.6%) | 36 | 35 | 6/6 · 6/6 |
| 8B | 13 (36.1%) | 26 (72.2%) | 36 | 36 | 6/6 · 6/6 |
| 32B, prior run | 11 (30.6%) | 32 (88.9%) | 36 | 36 | 6/6 · 6/6 |

All four new sizes returned every assigned request: 336 outputs, including 48
explicit controls. The earlier 32B run adds 84, making 420 outputs across the
five sizes. Returned does not mean parsed. I1 failures were:

- **0.6B:** 35 off and 11 on invalid final answers; no capped/non-EOS output.
- **1.7B:** 12 off invalid answers; four on invalid answers and one capped/non-EOS.
- **4B:** one on capped/non-EOS output; all off answers parsed.
- **8B and 32B:** all I1 outputs completed and parsed in both modes.

For 8B the paired on-minus-off difference is **+36.1 percentage points**, with a
95% paired scenario-bootstrap interval of **[+13.9, +58.3]**. The archived 32B
difference is **+58.3 points [38.9, 77.8]**. The bootstrap resamples the same 36
base identities jointly across modes, using 20,000 replicates and seed
2026110503. These describe this fixed cohort, checkpoint and single-sample policy.
The frozen analysis issues no paired interval for incompletely parsed sizes;
their apparent gaps must not be presented as clean inference-only comparisons.

## Why the 0.6B score looked so poor

The runtime succeeded: all 84 outputs reached EOS, the profile and admission gates
passed, preemption checks passed, and GPU memory returned to baseline. There is
no evidence here of a timeout, transport loss or power interruption causing its
low score. Worker elapsed time was 1,958.67 seconds (32 minutes 38.67 seconds).

The frozen parser accepts a single A/B/C letter, optional period, and whitespace.
The model often generated **`B: shorter delivery time`** instead. In a post-hoc
syntax audit, **34 of the 40 invalid off-mode outputs** (I1 plus controls) matched
exactly a letter, colon and criterion description. Other invalid outputs included
explanations, multiple option lines, or contradictory answers. This audit explains
format failure; it does not replace the parser or assign repaired answers.
Thinking-on outputs also sometimes added text after the closing think block.

Format is not the whole explanation. The separately collected, prospectively
specified first-position candidate-label scores select the correct I1 label on
**12/36 off-mode items**, equal to the nominal three-class chance reference.
Thus strict off-mode **0/36 is not evidence of zero criterion knowledge**; the
label-score diagnostic still shows weak discrimination on these items. The six
explicit off-mode controls score 5/6 by candidate argmax, compared with 1/6 under
the strict whole-answer parser. Neither measure silently substitutes for the other.

Some inspected traces also confuse numeric comparisons or attend to irrelevant
archive tags. Those examples motivate further task analysis; they do not establish
a general internal cause of failure. No systematic trace-coding claim is made.

## Continuous first-position scores

For every new off-mode I1 item, the first generated position records raw vLLM
A/B/C log-probabilities. Normalize only over those three labels. This provides
an encoding-consistent descriptive measure even when later text violates the
answer format. The argmax below uses those recorded scores, not extracted prose.
For this descriptive table, ties receive no credit and are reported separately;
this analysis convention does not alter the frozen sampled-answer parser. One
top-label tie occurred at each of 1.7B and 4B.

| Size | Scored off items | Candidate-label argmax correct | Mean correct-label probability | Mean correct-label log-probability |
| --- | ---: | ---: | ---: | ---: |
| 0.6B | 36/36 | 12/36 | 0.319 | −2.146 |
| 1.7B | 36/36 | 11/36 | 0.308 | −4.684 |
| 4B | 36/36 | 10/36, plus one tie | 0.299 | −3.906 |
| 8B | 36/36 | 13/36 | 0.357 | −3.059 |
| 32B | Not collected | Not available | Not available | Not available |

Candidate normalization conditions on the three labels; it is not full-vocabulary
answer probability or a calibrated capability estimate. These engine-native
values do not inherit the PyTorch FP32-head qualification certificate. On-mode
scores are available only for parsed final answers: 25/36, 31/36, 35/36 and 36/36
at 0.6B, 1.7B, 4B and 8B. Their mean correct-label probabilities are respectively
0.357, 0.419, 0.571 and 0.722. Those changing subsets prevent a clean all-item
calibration comparison. Full counts and log-scores remain in the machine-readable
summary; missing historical 32B values are not imputed.

## What this changes

The original blanket reading that 8B cannot recover these criteria is too broad:
with the adequate 8,192-token allowance, its native thinking mode recovers 26/36.
Its earlier 1,024-token run remains censored, and its earlier single-pass findings
retain their original scope. The 8B result nevertheless misses the frozen
operational reliability gate: its overall Wilson lower bound is 0.560, below
0.600 (28/36 would have cleared it). Its true-none lower bound passes, and all
controls pass. **32B remains the prospectively selected purchasing platform.**
This selection is not authorization for another job or automatic qualification
of 32B hooks or long-trace choice scoring.

The strongest current evidence is **mode-dependent report recovery**. Native modes
change the prefix as well as allowing generated reasoning; neither this gap nor
the observed size ordering isolates computational necessity. Size also covaries
with training recipe. A correct report concerns the archive criterion, not proof
of attributing that goal to the present evaluator. The study has not yet tested
thinking-on purchasing behavior, causal internal dissociation, or monitor uplift.

The report therefore supports the proposal's availability-versus-articulation
question and an internal-readout followup. It does not establish that activations
lack criterion information in off mode, that reasoning traces are necessary for
monitoring, or that unmentioned criteria influence purchasing. Fresh scenarios,
held-out layouts, separate in-context report checks and causal controls remain
prospective. I2 is excluded from new work because of score-polarity ambiguity;
I3 and test data remain sealed. Negative and incomplete results are retained.

## Execution and cost

The four new sizes use pinned Qwen3 weights/tokenizers, vLLM 0.32.0, the same
frozen paired requests, seeds, groups and sampler, and the 8,192-token cap. The
hardware gate requires A100-SXM4-80GB, driver 610.57.04 and CUDA 13.0. There is no
claim of token identity under a different batch schedule. Primary scoring used
the frozen parser; it was not revised after observing small-model outputs.

The first bridge attempt stopped on the power guard during synthetic profiling,
before criterion generation. Attempt two completed 8B, 4B and 1.7B, then refused
0.6B measurement at its resource admission gate: 9,927 seconds required versus
8,306.92 remaining. That refusal was scheduling evidence, not a capability result.
The separately approved 0.6B job repeated full profiling and measured only 0.6B,
using the exact cached image and GPU settings, with declared host RAM reduced
from 96 to 32 GiB. Its first local launch failed SDK registration before creating
an app or allocating resources; that zero-cost failure is preserved. No automatic post-load retry or outcome-based resubmission was used; the second
bridge attempt was explicitly authorized after a zero-research profiling stop.

| Bridge execution | Posted all-resource usage |
| --- | ---: |
| Original power-guard stop | $0.79049215 |
| Shared worker: 8B, 4B, 1.7B and 0.6B profile | $12.20082939 |
| Standalone 0.6B, including repeated profile | $1.55675223 |
| Total bridge usage | **$14.54807377** |

**Project metered cloud usage is $31.18 against the $100 ceiling; external API
billing is pending.** Two independent provider snapshots agree after the final
app-hour closed, including startup and all reported resource charges. The $24
and $10 holds were replaced by actual posted usage; $33 in older holds remains
separate from spending. These are metered figures, not final invoices; late
provider adjustments require updates. No further paid launch is authorized here.

## Reproduction and preserved evidence

- Combined stopped-run analysis: `outputs/bridge-sweep-final-v1/combined-analysis.json`.
- Continuous/count summary: `outputs/bridge-sweep-final-v1/summary.json`.
- Post-hoc syntax audit, with zero repaired outcomes: `outputs/bridge-sweep-final-v1/06b-format-diagnostics.json`.
- Original analyses and raw committed frames: `outputs/bridge-sweep-run-v2/` and `outputs/bridge-06b-run-v2/`.
- Frozen executable cohort: `outputs/bridge-sweep-ready-v6/`; standalone extension: `outputs/bridge-06b-ready-v2/`.
- Plot source and count metadata: `scripts/plot_bridge_sweep.py` and `docs/proposals/figures/qwen3-mode-response-sweep-v1.json`.
- Posted project accounting: `data/costs/bridge-completion-project-usage-v1.json` and the per-app reconciliation reports.

The prior 32B estimate and the existing Sol result remain separately sourced.
The new report and proposal revision receive a new SHA-256 manifest/archive;
earlier proposal and experiment freezes are preserved.
