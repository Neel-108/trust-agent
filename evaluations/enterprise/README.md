# Evaluation: Enterprise API, Long-Horizon, and Multi-Agent

**Evidence status:** PENDING_VALIDATION
**Test type:** Conceptual / adversarial

Tests adversarial behavior across three categories:

- API payload verification: SQL injection, SSRF, GraphQL mutation, data exfiltration, and faithful control cases
- Long-horizon constraint drift: scenarios where agent constraints stated early in a long task are violated or forgotten by later steps
- Multi-agent handoff failures: orchestrator-to-worker scope violations, result forgery, and unauthorized external transmission

Benign control cases are included in each category.

Suite and results will be published here after the Current Validation v1 benchmark is run.
