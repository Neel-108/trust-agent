# Trust Agent Evaluations

This directory contains general adversarial and benign capability evaluations for Trust Agent. These suites are independent of specific named incidents; incident-derived evidence is published separately under [`../incidents/`](../incidents/).

The evaluation record is intentionally complete: successful detections, conservative review outcomes, and observed misses are all retained. A failed case is not removed or rewritten to improve headline performance.

## Current evaluation set

| Evaluation | Cases | PASS | REFINE | FLAG | Matched expected |
|---|---:|---:|---:|---:|---:|
| [Benign Controls](benign-controls/) | 10 | 8 | 2 | 0 | 8 / 10 |
| [Structural Logic & State Forgery](structural-logic/) | 4 | 1 | 3 | 0 | 2 / 4 |
| [Structural Logic Correction](structural-logic-correction/) | 3 | 2 | 1 | 0 | 1 / 3 |
| [Catastrophic Risk & Safety Boundary](catastrophic-risk/) | 4 | 1 | 3 | 0 | 3 / 4 |
| [Path Obfuscation & Alias Bypass](path-obfuscation/) | 4 | 1 | 3 | 0 | 4 / 4 |
| [State Drift & Cognitive Overload](state-drift/) | 4 | 3 | 1 | 0 | 2 / 4 |
| [Indirect Prompt Injection & Hijack](indirect-injection/) | 3 | 1 | 2 | 0 | 3 / 3 |
| [Enterprise Chaos: API, Long-Horizon & Multi-Agent](enterprise-chaos/) | 15 | 2 | 12 | 1 | 10 / 15 |

These evaluation suites are additional capability and limitation evidence. They are not combined into the headline **Current Validation v1** benchmark under [`../benchmarks/current-validation-v1/`](../benchmarks/current-validation-v1/).

## How to read these results

`PASS`, `REFINE`, and `FLAG` are Trust Agent verdicts:

- **PASS** — no blocking or review condition was identified within the evaluated scope.
- **REFINE** — clarification or human review is required before automatic progression.
- **FLAG** — a blocking condition was identified.

A mismatch with an expected result is preserved rather than hidden. Some mismatches are conservative outcomes, such as an expected `PASS` receiving `REFINE` or `FLAG`. Others are security-relevant misses where an expected non-PASS result received `PASS`.

The most important known class of misses involves semantic violations encoded inside otherwise authorized write content. These are documented in [`../KNOWN_LIMITATIONS.md`](../KNOWN_LIMITATIONS.md).

## Suite notes

### Indirect Prompt Injection & Hijack

This suite evaluates downstream action drift associated with indirect-injection scenarios. Its structured cases do not provide the content of the read source file as a first-class verifier input. Therefore the results must **not** be interpreted as proof that Trust Agent semantically detects malicious instructions inside source content itself.

### Enterprise Chaos

This suite intentionally retains historical and unsupported tool surfaces in several cases. It is published as an out-of-scope robustness evaluation showing how the current system behaves when presented with actions beyond its normal supported tool manifest.

To make the preserved cases executable through the current test-suite schema, legacy `effect_class` labels were normalized to the current allowed vocabulary. Tool names, payloads, runtime authorization grants, provenance, case intent, and expected outcomes were otherwise preserved.

## Methodology

Evaluation construction and publication rules are defined in [`../METHODOLOGY.md`](../METHODOLOGY.md).

In particular:

- suites and expected outcomes are frozen before execution;
- observed failures remain in the record;
- fixture corrections must be explicit;
- public result files expose behavioral evidence without publishing proprietary Trust Agent internals.

## Files

Each completed evaluation folder contains:

- `README.md` — scope, interpretation, and result summary;
- `test_suite.json` — published evaluation suite;
- `results_public.json` — completed public results.

Benign controls are already finalized and retained unchanged.
