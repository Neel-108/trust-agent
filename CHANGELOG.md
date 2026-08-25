# Changelog

---

## v0.1.1 — 2026-08-25

Current evaluation evidence and repository organization update.

- Seven previously developed conceptual evaluation suites rerun through the current Trust Agent validation interface and published with fresh public results:
  - Structural Logic & State Forgery
  - Structural Logic Correction
  - Catastrophic Risk & Safety Boundary
  - Path Obfuscation & Alias Bypass
  - State Drift & Cognitive Overload
  - Indirect Prompt Injection & Hijack
  - Enterprise Chaos: API, Long-Horizon & Multi-Agent
- `evaluations/` reorganized around the completed named suites rather than pending category placeholders
- Benign controls retained unchanged
- `evaluations/README.md` added as the evaluation index
- `VALIDATION_STATUS.md` updated with current conceptual-evaluation results and incident-derived result summaries
- `KNOWN_LIMITATIONS.md` updated with freshly confirmed opaque write-content semantic misses and broader long-horizon drift failures
- Enterprise Chaos legacy `effect_class` vocabulary normalized for compatibility with the current test-suite schema; original tool names, case intent, payloads, runtime grants, provenance, and expected outcomes preserved
- OpenAI / Hugging Face incident evaluation included in the current incident evidence set
- Root documentation updated to distinguish the frozen Current Validation v1 benchmark from additional current-stack evaluation evidence

---

## v0.1.0 — 2026-08-19

Initial public release.

- Root documentation published: README, CAPABILITIES, METHODOLOGY, KNOWN_LIMITATIONS, VALIDATION_STATUS, CHANGELOG
- Current Validation v1 benchmark published: 10 adversarial cases, 10 benign controls, full results
- Incident folders published: novee, ghostjacking, agentjacking, opencode, pocketos
- Evaluation folders published: enterprise, structural, authorization, destructive-actions, benign-controls, multi-agent, provenance
- Enforcement evidence published: execution-permit primitive (6/6), integrated end-to-end (2/2)
- Current validation report published
