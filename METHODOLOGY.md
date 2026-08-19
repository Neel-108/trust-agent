# Trust Agent : Testing Methodology

This document describes how Trust Agent validation evidence is produced and structured.

---

## Core principle: Freeze before running

A benchmark must be frozen before it is run. The sequence is:

1. Select cases
2. Define expected outcomes for each case
3. Record sources
4. Freeze the suite, including version identifier
5. Run it
6. Retain all results, including failures

A failed case is not removed. A correctly constructed test that Trust Agent fails becomes a documented limitation or a regression target. Silent modification of failed cases after the fact is not permitted. A legitimate fixture error may be corrected only with explicit documentation of what changed and why.

---

## Types of test cases

Each test case is classified into one of four categories. This classification is stated in all published suite files and must not be overstated.

**Exact replay** — The published attacker payload or exact action sequence is reproduced without modification. Only used when the source provides sufficient published detail to justify this claim. Never described as exact replay when it is not.

**Incident-derived adaptation** — The mechanism of a real incident is preserved, but synthetic placeholders replace real credentials, domains, tokens, and identifiers. The attack class and structural properties are faithful to the source. This is the most common type used in incident folders.

**Synthetic projection** — Uses a real incident's threat model as a starting point but adds structure or scenarios not directly described by the source. Always labeled as such.

**Conceptual test** — Built from general threat models, not a specific incident. Used in evaluation folders rather than incident folders.

---

## Source quality

For incident-derived testing, sources are used in this order of preference:

1. Vendor security advisory
2. CVE / NVD
3. Original security research publication
4. Academic paper
5. Reputable secondary reporting, only when primary source is unavailable

Source URLs, researcher names, and publication dates are preserved in incident documentation. Tests are not built from unsourced social media claims.

---

## Incidents vs evaluations

**[incidents/](incidents/)** contains test suites derived from specific, named real-world security incidents or research disclosures. Each folder documents: the real incident, the source, which part was converted into a test, what adaptations were made, what was expected, what happened, what the result demonstrates, and what it does not demonstrate.

**[evaluations/](evaluations/)** contains general adversarial and benign capability tests developed independently of specific incidents. These cover threat categories rather than named incidents.

---

## Benign controls

Every validation benchmark includes benign control cases, legitimate actions that should not be blocked.

A system that blocks everything is not useful. Benign controls are not cosmetic. Their passage is part of what makes a positive adversarial result meaningful, and their failure is a calibration problem that must be documented.

---

## Synthetic safety

All test payloads use synthetic placeholders. No test suite published in this repository contains:

- Real credentials, tokens, or API keys
- Real domain names or hostnames targeted for attack
- Real customer data
- Payloads intended for execution against live services

Reserved test domain suffixes and documentation IP ranges are used in place of real targets.

---

## Public results format

Results published in this repository use the Trust Agent public results format. Each published result includes:

- Verdict per case: PASS, REFINE, or FLAG — with corresponding recommendation ALLOW, REVIEW, or BLOCK
- Expected outcome
- Match or mismatch with expected
- Public audit record per case, covering: verdict, reason code, per-category assessment, and operational meaning

The public format does not include internal scoring detail, engine architecture, calibration data, prompts, or proprietary mechanism information.

---

## What this repository does not claim

- "Actual incident replay" is not claimed when a synthetic adaptation was used
- "Real-world proof" is not claimed for an in-memory test harness
- "Live-agent proof" is not claimed until such a test exists
- Historical results are not presented as evidence of the current system without explicit labeling
