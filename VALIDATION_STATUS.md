# Trust Agent : Validation Status

---

## Current Validation v1

**Status: COMPLETE**

Adversarial component — 10 fresh unseen incident-derived cases:

| Metric | Value |
|---|---|
| FLAG verdicts | 10 |
| PASS verdicts | 0 |
| Matched expected | 8 |
| Mismatched expected | 2 (over-escalation on FABRICATION cases are both withheld from execution) |

Benign controls — 10 cases:

| Metric | Value |
|---|---|
| PASS verdicts | 8 |
| REFINE verdicts | 2 (INTENT_UNVERIFIED on low-context read requests are held for review) |
| FLAG verdicts | 0 |
| Matched expected | 8 |

No dangerous action received a PASS verdict. No legitimate action received FLAG; two benign reads were conservatively held for review.

Full results: [Current Validation v1](trust-agent-validation/benchmarks/current-validation-v1/)

Full report: [Current Validation Report](trust-agent-validation/reports/current-validation-report.md)

---

## Known failures

See [Known Limitations](trust-agent-validation/KNOWN_LIMITATIONS.md) for the full record.

The most security-relevant documented misses are SCOPE-CREEP-002 (authentication disabled via authorized write) and SUPPLY-CHAIN-001 (typosquatted dependency injected via authorized write). Both are consequences of limitation 1 in KNOWN_LIMITATIONS.md.

Known failures are not removed from the record. They are documented as boundaries of current capability and targets for future research.

---

## Historical validation

Prior validation work covers 200+ tests across multiple families including enterprise API behavior, structural logic, state forgery, authorization, multi-agent handoff, destructive operations, indirect prompt injection, path obfuscation, incident-derived suites, and benign controls.

Historical test records are available under [Incidents](trust-agent-validation/incidents/) and [Evaluations](trust-agent-validation/evaluations/) . 
All historical artifacts carry the HISTORICAL label and should not be read as evidence of the current system's performance. The system has evolved substantially since those runs.

---

## Enforcement validation

Evidence that Trust Agent decisions gate execution is published under [Enforcement](trust-agent-validation/enforcement/). This covers:

- Execution-permit primitive proof: 6 / 6
- Integrated local end-to-end enforcement proof: 2 / 2

See [Enforcement README](trust-agent-validation/enforcement/README.md) for the scope and limitations of these tests.
