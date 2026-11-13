# Hosted recovery-boundary check — frozen results

**November 9, 2026 (America/Caracas).** The fixed model list has finished.
The check did **not establish an immediate-recovery boundary**. GLM-4.5 and
DeepSeek-V3.1 recovered the criterion well with thinking enabled, but thinking-off
format failures prevent a clean comparison, especially for DeepSeek. The hosted
Qwen anchor was not measured. These are exploratory, strict-generation results,
not additions to the frozen five-size curve or a qualification of hosted inference.

## Strict results

Each completed configuration received the same 36 I1 items and six explicit
format controls in each mode. Correctness uses the frozen final-channel parser:
A/B/C with optional period/whitespace; no answer extraction from prose or traces.
Invalid or capped generations remain failures of the strict generation outcome.
Unattempted/provider-rejected items are reported separately, not as observed errors.

| Fixed configuration | I1 off: correct / 36 | Off: parsed / 36 | I1 on: correct / 36 | On: parsed / 36 | Explicit controls, off / on |
| --- | ---: | ---: | ---: | ---: | --- |
| Qwen3-32B / DeepInfra FP8 | Not measured | Not measured | Not measured | Not measured | Not measured |
| GLM-4.5-Air / Novita bf16 | Incomplete | Incomplete | Incomplete | Incomplete | Not measured |
| GLM-4.5 / Z.AI FP8 | 9 / 36 | 25 / 36 | 32 / 36 | 34 / 36 | 6/6 and 6/6 |
| DeepSeek-V3.1 / CoreWeave FP8 | 0 / 36 | 0 / 36 | 31 / 36 | 35 / 36 | 6/6 and 6/6 |

GLM-4.5 had eleven off-mode format failures and two on-mode capped/non-stop
responses. DeepSeek had 36 off-mode format failures and one on-mode capped/non-stop
response. DeepSeek's strict 0/36 is **a format-compliance result**, not evidence
that it cannot recover the criterion. Neither invalid output is rescored through
a parser written after seeing the responses. No candidate-label scores were
available in this hosted design. GLM's nine correct answers among 25 parsed
outputs is descriptive only; the parsed subset is selected by model output.

## Was off-mode output immediate?

“Bare letter” here means exactly A, B or C apart from whitespace, with no period.
The joint count additionally requires a stop/parsed response, explicitly reported
zero reasoning tokens and no visible separate reasoning. Missing token counts
are never treated as zero.

| I1 off-mode diagnostic | GLM-4.5 | DeepSeek-V3.1 |
| --- | ---: | ---: |
| Responses with explicitly reported zero reasoning tokens | 36 / 36 | 36 / 36 |
| Responses with visible separate reasoning | 0 / 36 | 0 / 36 |
| Bare letter + zero reported reasoning + no visible reasoning | 25 / 36 | 0 / 36 |
| Correct within that joint count | 9 / 25 | Not estimable (zero bare-letter responses) |
| Final-answer character range | 1–1,954 | 2,469–8,760 |
| Missing reasoning-token reports | 0 / 36 | 0 / 36 |

Across all off-mode research responses, including the six explicit controls, the
joint bare-letter counts are **31/42 for GLM-4.5** and **6/42 for DeepSeek**.
Every explicit control was a correct bare letter with zero reported reasoning.
Both providers thus obeyed the output format on the explicit controls; DeepSeek
failed that same format on every I1 off-mode item. All raw final texts, lengths,
completion counts and reported reasoning-token counts remain available by item.
These API observations do not prove a single forward pass, absence of internal
computation, or computational necessity. In particular, zero reported reasoning
with a long final response is not an immediate answer.

## Anchor and partial configurations

The predeclared hosted Qwen anchor bands were **6–17/36 off** and **28–36/36 on**,
with all research outputs parsed and 6/6 controls in each mode. They were
**not assessed**: the first synthetic off-mode call produced 397 reported reasoning
tokens, no final answer and a length stop at the 512-token cap. No anchor research
prompt was submitted. Its comparison record contains zero attempted items; those
zeros are not an accuracy estimate and do not demonstrate a mismatch with either
accuracy band. The off-mode preflight failed, so hosted/local comparability was
not established. The other fixed targets ran regardless, as prospectively required.

GLM-4.5-Air passed four synthetic mode checks, produced one research response that
failed the strict final-answer format, then returned HTTP 400 on the next request.
Its remaining requests were not submitted. The rejection's cause is unconfirmed;
no seed, provider or request parameter was changed and no request was retried.
There is no full-cohort estimate for this configuration.

## Execution, scope and cost

There were **183 POSTs**, across three local coordinator receipts sharing one
approved $6 reservation: 13 synthetic calls, 169 successful research responses
and one rejected research call. GLM-4.5 and DeepSeek each completed all 84 research
calls. No request was resubmitted; no outcome remains transport-unknown. Known
saved mode/request failures skipped only their configuration. Raw failures and
partial data are preserved, not removed from the record.

Cumulative conservative response/tariff usage is **$0.45778580**. A post-run,
read-only key lookup showed **$0.455852885** usage at that observation; it is not a
final invoice reconciliation. The receipt retains **$0.10059776** of unresolved
rejection-billing exposure, which is not actual spend. The $6 reservation remains
held pending reconciliation. No credit purchase, account-limit change or GPU
expense belongs to this API job.

The endpoints use different architectures, precisions and opaque hosted templates;
this is not a dense Qwen scale threshold. The failed anchor adds a comparability
limitation. High on-mode report accuracy supports cue recovery in these hosted
configurations, but no clean high-performing immediate arm emerged under the
frozen parser. These report tasks do not measure purchasing transfer or causal
activation effects. Proposal revision 5 and the sealed I3 manifest remain unchanged.
The separately approved purchasing synthetic profile is the next infrastructure
step; no purchasing research outcome has been generated.

Machine-readable results: `outputs/hosted-boundary-analysis-v1.json`.
Raw attempts: `outputs/hosted-boundary-run-v{1,2,3}/`.
Offline summary: `scripts/summarize_hosted_boundary.py` (three targeted tests;
388 tests passed in the full pre-analysis suite). It refuses to analyze an active
coordinator, rejects duplicate responses, and distinguishes missing/rejected items
from observed strict failures.
