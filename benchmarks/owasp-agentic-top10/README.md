# OWASP Agentic Top 10 Benchmarks

This directory contains Trust Agent challenge suites organized against the **OWASP Top 10 for Agentic Applications**.

The purpose of this benchmark family is to evaluate Trust Agent against externally defined agent-security risk categories using documented real-world incidents, vulnerability disclosures, and published security research. Cases are not selected from Trust Agent's observed outputs and are not rewritten after their first run.

## Benchmark policy

Each released version is treated as a frozen batch.

- A version is frozen before its first execution.
- Once results are observed, cases in that version are not added, removed, rewritten, or retuned.
- Newly discovered OWASP-relevant incidents or research become a **new version** (`v2`, `v3`, and so on).
- Earlier versions and their failures remain preserved.
- Each case records its source and the security property preserved by the synthetic adaptation.
- Synthetic adaptations avoid real credentials, live attacker infrastructure, customer data, and destructive production targets.

This versioning rule is important: the benchmark is intended to measure performance on previously unseen batches rather than become a corpus that is continuously tuned against the verifier.

## Current versions

| Version | Cases | Coverage | Status |
|---|---:|---|---|
| [version 1](./v1/) | 10 | One incident-derived case for each ASI01–ASI10 category | Frozen and completed |



## Evidence classification

These suites are **framework benchmarks with incident-derived cases**.

They are kept under `benchmarks/` rather than `incidents/` because a single OWASP suite can combine multiple unrelated incidents, disclosures, and research findings. The incident provenance of each individual case is retained in `source.md` and in the test-suite metadata.

This is different from a named incident folder, which evaluates one specific incident family, and from a generic conceptual evaluation, which may not be tied to real-world evidence.

## Interpretation

OWASP category coverage does not mean complete mitigation of an OWASP risk class. A case demonstrates only how the tested system behaved on that particular frozen scenario.

Results should therefore be reported with:

- exact expected-outcome match;
- observed verdict distribution;
- automatic-execution intervention rate;
- unsafe automatic allows;
- over-escalations; and
- known limitations exposed by the run.

The benchmark is evidence, not a claim that every manifestation of an OWASP category is solved.
