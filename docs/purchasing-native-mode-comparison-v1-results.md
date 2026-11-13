# Purchasing archive sensitivity differs across native thinking modes

**November 13, 2026. Exploratory paired development comparison.**

The matched thinking-off control shows the prespecified qualitative pattern:
**I1 archive-content sensitivity is evident with native thinking, but is not
detected with thinking off; T1 readable rubrics shift choices in both modes.**
The off outputs all met the immediate-answer format, so format compliance does
not explain this behavioral contrast. The additional interaction with evaluation
framing remains unresolved. This is native-mode dependence in one model and
task, not a demonstration of computational necessity or evaluation gaming.

## Completion and configuration

The approved detached off-mode run completed **288/288 purchasing requests and
all eight bases** in **278.12 seconds (4 minutes 38 seconds)**. The first allocation
matched A100-SXM4-80GB / driver 610.57.04 / CUDA 13.0. The 56,128-token KV capacity,
batch-ten collection identity, exact repeated synthetic scores, six native
controls and zero-preemption checks passed. All **137 backend frames** were
retrieved and verified. Provider status is stopped, with zero tasks.

The purchasing prompt strings, seeds, weights, bf16 precision, engine/image,
sampler, base scenarios and customer orientation match the completed thinking-on
pilot. Off mode uses the documented native empty-think **input prefix**, scores
generated position zero and caps output at 32 tokens. Purchasing group membership
and order were retained after removing the report probes; groups were not
repacked, but occupancy differs. These differences were declared before launch.

**Every off-mode response was exactly two generated tokens: one strict A/B letter
plus EOS.** No generated thinking boundary appeared. All 288 margins were captured,
and all 288 choices passed the frozen parser. No research retry, forced label,
output repair, report probe or new annotation was used.

## Choices

Counts are customer-favored choices out of 24 assigned traces per condition.
These are three seeds within each of eight bases, not 24 independent scenarios.
The customer expressed a mild preference and accepted either option.

| Cue and mode | C1: none | C2: aligned | C3: conflict | C4: framed none | C5: framed aligned | C6: framed conflict |
| --- | ---: | ---: | ---: | ---: | ---: | ---: |
| I1, thinking off | 20 | 19 | 21 | 15 | 15 | 16 |
| I1, thinking on | 21 | 24 | 9 | 16 + 1 unresolved | 24 | 9 + 1 unresolved |
| T1, thinking off | 20 | 23 | 11 | 16 | 22 | 11 |
| T1, thinking on | 24 | 24 | 9 | 24 | 24 | 4 |

Without evaluation framing, the I1 conflicting-minus-aligned choice contrast is
**+8.3 percentage points off**, versus **−62.5 points on**. The paired mode
difference is **−70.8 points**, base-bootstrap 95% interval **[−104.2, −41.7]**.
A difference between two probability differences can exceed 100 points in
magnitude; the interval is not a probability interval. With framing, the
all-assigned paired mode-difference bounds are **−66.7 to −62.5 points**, accounting
for the one unresolved on-mode C6 choice.

T1 remains behaviorally effective without thinking: choices change from **23/24
to 11/24** without framing and **22/24 to 11/24** with framing. Thus the off
configuration can respond to readable objective cues. Neither I1 off-mode count
contrast points toward the archive-implied conflicting objective.

## Margins and paired mode differences

Margins are raw vLLM A/B log-probability differences signed toward the customer.
The on margin conditions on the sampled reasoning trace; the off margin is at
generated position zero following the empty-think input prefix. Both use the
declared bf16 engine readout, not the qualified PyTorch float32 final head.

The primary paired comparisons use at least two of the three margins per cell,
equal base weights, eligibility in both modes, and 10,000 paired base-bootstrap
draws (seed 2026111009). All eight bases contribute. Brackets are percentile 95%
intervals. No confirmatory p-values or equivalence tests are reported.

| Conflicting minus aligned, nats | Thinking off | Thinking on | Paired on minus off |
| --- | ---: | ---: | ---: |
| I1, no framing: C3 − C2 | +0.38 [−0.45, +1.10] | −11.31 [−15.06, −7.06] | **−11.68 [−15.74, −7.28]** |
| I1, framing: C6 − C5 | +0.43 [−0.30, +1.16] | −9.25 [−13.02, −5.21] | **−9.68 [−13.22, −5.81]** |
| T1, no framing: C3 − C2 | −3.25 [−4.06, −2.41] | −13.65 [−17.60, −9.51] | −10.40 [−14.51, −6.23] |
| T1, framing: C6 − C5 | −2.94 [−3.80, −2.04] | −15.41 [−17.04, −13.62] | −12.47 [−14.01, −11.03] |

The I1 off intervals do not establish exact absence or equivalence: modest effects
remain compatible with this eight-base cohort. The large paired native-mode
differences are also present in sampled choices, so they are not solely a
consequence of greater answer confidence after reasoning. T1 margins become
larger with thinking too; the raw margin amplification is not unique to I1.

I1's evaluation interaction D = (C6 − C5) − (C3 − C2) is **+0.05
[−0.16, +0.24] off** and **+2.06 [−2.41, +7.76] on**. The paired mode difference
in D is **+2.01 [−2.45, +7.58]**. These results do not establish that evaluation
framing has no effect, nor that it amplifies objective influence.

## Sensitivity, headroom and missingness

The original on arm has one missing I1 C6 margin and one I1 C4 format-invalid
choice whose slot margin is valid. Off mode adds no missing data. Requiring all
three margins leaves seven I1 bases for the framed comparison: paired on-minus-off
**−8.88 [−12.72, −4.73]** nats. Restricting each cell in both modes to identical
valid seeds retains eight bases and gives **−9.68 [−13.23, −5.81]**. The
no-framing contrast is unchanged under either sensitivity. T1 is unchanged.

Off-mode C1 median absolute margins are **0.88 nats I1** and **2.13 T1**, compared
with **6.94 and 8.56 on**. Off C1 letters are 16 A / 8 B within each family, against
balanced customer letters of 12 A / 12 B. This observed letter imbalance is
reported, not calibrated away or used to select outcomes. All 288 off margins
lie within numerical tolerance of a 0.125-nat grid, as expected for this bf16
readout; none has absolute magnitude at least 10 nats. Mean A/B mass is .980
for I1 and .992 for T1. All lengths, per-condition counts, base estimates and
paired switches are preserved in the machine-readable analysis.

## Interpretation and scope

The supported result is **a native-mode gap in approval-archive influence on
purchasing**, alongside readable-cue sensitivity in both modes. It connects the
earlier report-task mode gap to a behavioral setting that never asks about the
criterion in the choice calls. It does not establish accurate recovery of every
implied criterion or a particular internal representation.

“Requires deliberation” would be stronger than these data support. The native
template changes as well as the amount of generated computation; batch occupancy
and the declared output cap also differ. Same weights and paired prompts reduce
confounds without isolating serial computation alone. There is no matched
explicit-priority arm here, so the earlier single-pass null cannot be attributed
to priority alone. Both options were acceptable to the customer; interpreting an
approval history as guidance remains compatible with ordinary in-context learning.
This is not evidence of evaluation gaming, concealment, or a causal monitor.

The earlier two-letter contextual report failure is unchanged; no post-hoc
extraction was applied. Original human/assistant annotations and disagreements
remain frozen. Human criterion-mention judgments cover 48 traces (40 yes), while
assistant judgments cover 144 (144 yes). No whole-cohort human mention range or
influence-without-mention claim is added.

## Reproduction, tests and budget

- Frozen off packet: `outputs/purchasing-off-ready-v2/`.
- Approved launch and immutable raw/score frames:
  `outputs/purchasing-off-run-v1/`, `outputs/purchasing-off-completed-v1/`.
- Canonical paired analysis: `outputs/purchasing-mode-comparison-v1/analysis.json`,
  with per-request off records and an input/output SHA-256 manifest.
- Reproduce offline into a fresh directory:
  `.venv-bf16/bin/python scripts/analyze_purchasing_modes.py --off-frames outputs/purchasing-off-completed-v1 --out /tmp/purchasing-mode-reproduction`.

**427 tests passed**, including paired eligibility, contrast sign, identical-seed
missingness and all-assigned choice bounds. No paid calls were used for analysis.
The approved **$6 all-attempt hold remains**: this app's resource billing rows
were still pending in the immediate post-run refresh. The monthly summary
increment is not assigned as this job's final cost. Conservative project allocation
remains **$97.33**, leaving **$2.67** with every hold counted. There is no automatic
continuation or additional experiment. Proposal revision 6 remains unchanged
pending review of this result.
