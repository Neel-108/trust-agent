# Trust Agent 

Trust Agent is a runtime verification layer for AI agent outputs.

It sits between an agent's proposed action and execution. Before a consequential action runs, it independently evaluates one question: is this action authorized, aligned, and safe to execute?

The separation this enforces:

```
agent intelligence ≠ execution authority
```

An agent can be competent and still propose something the user did not authorize. Trust Agent evaluates the proposed action independently before execution authority is granted.

---

## How it works

```
Agent proposes action → independent verification → ALLOW / REVIEW / BLOCK → execution only when conditions are satisfied
```

---

## Current validation

Current Validation v1 is complete.

Fresh unseen adversarial cases: 10/10 FLAG, 0 PASS, 8/10 matched expected. 

Benign controls: 8/10 PASS, 2 REFINE, 0 FLAG, two legitimate low-context reads were held for review.

Full results and methodology are in [Current Validation v1](benchmarks/current-validation-v1/)

A separate [OWASP Agentic Top 10 benchmark](benchmarks/owasp-agentic-top10/) is also published. Its frozen v1 suite contains **10 previously unseen** incident-derived cases, one for each ASI01–ASI10 category. Observed results were 4 FLAG, 4 REFINE, and 2 PASS: **5/10 exact expected-outcome matches and 8/10 cases withheld from automatic execution**. The two unsafe PASS outcomes reproduced the documented opaque write-content semantic limitation.

Additional current-stack conceptual evaluations, including successful detections, conservative review outcomes, and documented misses, are published under [Evaluations](evaluations/). These are kept separate from the headline Current Validation v1 benchmark.

---

## Operational behavior

| Scenario | Outcome | Operational meaning |
|---|---|---|
| Compromised agent proposes destructive action | FLAG or BLOCK | Execution does not proceed in evaluated and mediated scope |
| Legitimate file operation sufficiently verified | ALLOW | Normal work proceeds without unnecessary blocking |
| Authorization scope is ambiguous | REVIEW | Agent cannot silently continue; human review required |
| Opaque write content (current limitation) | May pass | Limitation documented; see KNOWN_LIMITATIONS.md |

---

## Repository contents

| Path | Contents |
|---|---|
| [Incidents](incidents/) | Test suites derived from real-world disclosed security research |
| [Evaluations](evaluations/) | General adversarial and benign capability tests |
| [Benchmarks](benchmarks/) | Frozen validation releases and framework benchmarks, including OWASP Agentic Top 10 |
| [Enforcement](enforcement/) | Evidence that decisions actually gate execution |

---

## What is not in this repository

The Trust Agent engine, scoring logic, internal prompts, and calibration data are proprietary. This repository contains validation evidence and a behavioral description only, evidence of observed behavior and an honest account of where it currently does not perform as expected.

---

## Status

Built and tested by one person. Not yet independently audited. Validation is ongoing.

[![License: All Rights Reserved](https://img.shields.io/badge/license-All%20Rights%20Reserved-red)](LICENSE.md)

---

## Contact

Open to demonstration, evaluation, or collaboration.
Email: swapnilpanchal0215@gmail.com
