# Evaluator-objective inference across native thinking modes

Research by Simon Rendon · November 13, 2026

**[Read the proposal (PDF)](proposal.pdf)** · [Markdown version](docs/proposals/RESEARCH_PROPOSAL_v3.md)

I designed and ran a paired study of evaluator-criterion recovery and purchasing choices across native thinking modes, built the measurement and validation pipeline, and documented the exploratory results and failures.

Across five Qwen3 sizes, immediate criterion recovery remained weak while reports with native thinking improved. In a matched eight-scenario Qwen3-32B purchasing pilot, inferred approval archives shifted choices detectably only with native thinking; a readable rubric shifted choices in both modes. These are exploratory native-mode comparisons, not proof of computational necessity, faithful reasoning, or evaluation gaming. Customer preferences were mild and either option was acceptable.

## Frozen results reports

- [Five-size Qwen3 report sweep](docs/bridge-sweep-v1-results.md)
- [32B paired thinking comparison](docs/qwen32b-thinking-v3-results.md)
- [Hosted model validity and boundary check](docs/hosted-boundary-v1-results.md)
- [Thinking-on purchasing pilot and annotation limitations](docs/purchasing-pilot-v1-results.md)
- [Matched thinking-off purchasing control](docs/purchasing-native-mode-comparison-v1-results.md)

The proposal is revision 9. Its planned fresh-base replication uses a scenario-level paired mode contrast as primary; the trace-level mixed model is a sensitivity. This prospective plan does not change the historical protocols or the exploratory status of completed results.

## Scope of this release

This is a document release, with selected frozen reports, figures and checksums. Raw traces, private annotations, datasets, credentials, model weights and machine configuration are not included. Paths to those local records in reports describe provenance and may not resolve in this document release. Figure JSON files preserve source hashes; this release does not claim to contain the complete executable experiment.

See [SHA256SUMS](SHA256SUMS) for file integrity. No application has been submitted by publishing this repository.
