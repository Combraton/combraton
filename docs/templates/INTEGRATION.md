# Integration evidence

Template, not a claim that any integration has run. For initial standalone validation, Combraton is explicitly absent; record Protocol, PIO, CBR and benchmark/fixture revisions. Later control-plane evaluations add Combraton.

## Journey

Feature/acceptance link, expected outcome, distinguishing negative case and reserved human judgment.

## Tested combination

| Component | Commit / release | Real, simulated or absent |
|---|---|---|
| Protocol | Fill exact revision | |
| PIO | Fill exact revision | |
| CBR | Fill exact revision | |
| Benchmarks / fixture / scorer | Fill exact revision | |
| Combraton | Absent for standalone gate; otherwise exact revision | |
| Harness / model / adapter | Fill actual versions | |

## Reproduction and observations

Record environment/OS, fixture/input identity, isolated resources, actual setup/run/check commands, exit codes and durable artifact links. Include relevant packet, invocation, receipt and observation references once those APIs exist. Do not invent API field names from this template.

Record the success case and affected failure/recovery cases, including any source correction, missing required context, lost acknowledgment or restart. State what was not tested.

## Review and acceptance

Review base/head per affected PR, concrete findings and fixes, current compatibility limitations, actual human decision/authority when required. Individually passing tests do not certify the combination. If a revision changes, rerun affected integration checks or explicitly mark this evidence historical.

Use the [benchmark run record](https://github.com/Combraton/benchmarks/blob/main/docs/RUN-RECORD.md) for comparative trials. A conformance pass and a task-quality result are separate claims.
