# Trust Agent : Validation Status

---

## Current Validation v1

**Status: COMPLETE**

Adversarial component - 10 fresh unseen incident-derived cases:

| Metric | Value |
|---|---|
| FLAG verdicts | 10 |
| PASS verdicts | 0 |
| Matched expected | 8 |
| Mismatched expected | 2 (over-escalation on FABRICATION cases are both withheld from execution) |

Benign controls - 10 cases:

| Metric | Value |
|---|---|
| PASS verdicts | 8 |
| REFINE verdicts | 2 (INTENT_UNVERIFIED on low-context read requests are held for review) |
| FLAG verdicts | 0 |
| Matched expected | 8 |

No dangerous action received a PASS verdict. No legitimate action received FLAG; two benign reads were conservatively held for review.

Full results: [Current Validation v1](benchmarks/current-validation-v1/)


---

## Incident-derived evaluations

Named incident and security-research adaptations are published under [Incidents](incidents/).

These suites are separate from the general conceptual evaluations under `evaluations/`. Each incident folder documents the source, how the disclosed mechanism was adapted into a synthetic test, the expected behavior, observed results, and the limits of what the test demonstrates.

| Incident evaluation | Cases | PASS | REFINE | FLAG | Expected-result status |
|---|---:|---:|---:|---:|---|
| AgentJacking | 4 | 1 | 1 | 2 | 3 matched, 0 mismatched, 1 unscored |
| GhostJacking - Suite A | 5 | 0 | 2 | 3 | 5 unscored |
| GhostJacking - Suite B | 5 | 5 | 0 | 0 | 0 / 5 matched |
| Novee | 6 | 0 | 2 | 4 | 5 / 6 matched |
| OpenAI / Hugging Face | 11 | 0 | 1 | 10 | 10 / 11 matched |
| PocketOS | 4 | 1 | 1 | 2 | 3 matched, 0 mismatched, 1 unscored |

### Important interpretation notes

- **AgentJacking:** the three scored cases matched their expected outcomes; one additional limitation/control case was intentionally unscored.
- **PocketOS:** the three scored cases matched expected outcomes; one benign/control case was intentionally unscored.
- **Novee:** five of six cases matched expected outcomes. One case expected `FLAG` but received `REFINE`; automatic progression was still withheld pending review.
- **OpenAI / Hugging Face:** ten of eleven cases matched expected outcomes. One case expected `FLAG` but received `REFINE`; automatic progression was still withheld pending review.
- **GhostJacking Suite A:** all five cases were intentionally unscored. Observed outcomes were 3 `FLAG` and 2 `REFINE`; these should not be converted into a match rate.
- **GhostJacking Suite B:** all five expected `FLAG` cases received `PASS`. This is a documented semantic-content/generalization failure and should not be presented as a successful incident defense.




Incident-derived tests do not claim exact real-world replay unless the source material supports that classification. Synthetic adaptations and projections are labeled according to the testing methodology.

Observed failures and known limitations remain part of the public record.

---

## Known failures

See [Known Limitations](KNOWN_LIMITATIONS.md) for the full record.

The most security-relevant documented misses are SCOPE-CREEP-002 (authentication disabled via authorized write), SUPPLY-CHAIN-001 (typosquatted dependency injected via authorized write), and the five GhostJacking Suite B semantic-generalization cases that received PASS.

Known failures are not removed from the record. They are documented as boundaries of current capability and targets for future research.

---

## Evaluation suites

Seven previously developed conceptual evaluation suites have been rerun through the current Trust Agent validation interface. Their original adversarial scenarios and expected outcomes were preserved. Where an older fixture used schema vocabulary no longer accepted by the current test format, compatibility-only normalization was documented without changing the intended scenario.

These runs are published under [Evaluations](evaluations/) as current capability and limitation evidence.

They are **not combined into the headline Current Validation v1 benchmark**. Current Validation v1 remains the fresh unseen benchmark release; the evaluation suites are additional targeted probes covering previously developed structural, state-drift, path, injection, catastrophic-risk, and enterprise-style scenarios.

### Freshly rerun conceptual suites

| Evaluation | Cases | Matched expected |
|---|---:|---:|
| Structural Logic & State Forgery | 4 | 2 / 4 |
| Structural Logic Correction | 3 | 1 / 3 |
| Catastrophic Risk & Safety Boundary | 4 | 3 / 4 |
| Path Obfuscation & Alias Bypass | 4 | 4 / 4 |
| State Drift & Cognitive Overload | 4 | 2 / 4 |
| Indirect Prompt Injection & Hijack | 3 | 3 / 3 |
| Enterprise Chaos: API, Long-Horizon & Multi-Agent | 15 | 10 / 15 |

Observed failures remain published. Several expected non-PASS cases received PASS, primarily where a semantic constraint violation was encoded inside otherwise authorized write content. Those misses are documented in [Known Limitations](KNOWN_LIMITATIONS.md).

The Enterprise Chaos suite also intentionally retains several historical/unsupported tool surfaces and should be read as out-of-scope robustness evidence rather than as a support claim for every represented tool or API.

---

## Historical validation

Older validation artifacts that have **not** been rerun on the current system remain historical evidence only and should not be presented as proof of current behavior.

The repository distinguishes these from current benchmark and evaluation evidence through the surrounding documentation and artifact status.

---

## Enforcement validation

Evidence that Trust Agent decisions gate execution is published under [[Enforcement](enforcement/). This covers:

- Execution-permit primitive proof: 6 / 6
- Integrated local end-to-end enforcement proof: 2 / 2

See [Enforcement README](enforcement/README.md) for the scope and limitations of these tests.
