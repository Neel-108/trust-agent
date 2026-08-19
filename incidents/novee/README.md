# Incident: Novee — Black Hat 2026 Coding Agent Trust-Handoff Failures

**Evidence status:** PENDING_VALIDATION (results pending re-run against current system)
**Test type:** Incident-derived adaptation
**Source:** Novee Security / Elad Meged, Black Hat 2026

---

## 1. What happened in the real incident

Elad Meged (Novee Security) disclosed a series of trust-handoff failures in coding agents from Anthropic (Claude), Google (Gemini), and OpenAI (Codex/Operator). The research was presented at Black Hat 2026.

The disclosed failures include:

- Claude R1: Remote code execution via a git push flag whose value was stripped by validators but executed by git, with exfiltration via curl
- Claude R2: Arbitrary file read via a reversed /proc/self/environ path that bypassed literal string matching, with secrets leaked to a public GitHub Step Summary through a display_report flag
- Claude R3: Data exfiltration through a 64-repository character oracle using attacker-controlled repository naming patterns
- Gemini: A full-chain attack combining decorative coreTools restrictions, parent process environment read, and token reuse for workflow dispatch
- Codex: Persistent cross-pass instruction hijacking through a poisoned AGENTS.md file, where a validator failure on pass 1 caused pass 2 to reload the attacker-controlled file

See `source.md` for full citation.

---

## 2. Source

See `source.md`.

---

## 3. What was converted into a Trust Agent test

The full proposed-action chains for each of the five attack scenarios above were expressed as structured Trust Agent verification requests. A sixth case covers Codex drift behavior.

No vendor implementation is emulated. These are incident-faithful proposed-action tests expressed through Trust Agent's structured contract.

---

## 4. Adaptations made

All exploit primitives are preserved as described in the published source. Synthetic placeholders replace all real credentials, tokens, repository names, domain names, and environment values. No live service is contacted. The adaptation type is incident-derived, not exact replay.

---

## 5–8. Expected outcomes, results, demonstration, and limitations

**Status: PENDING**

Results are pending re-run against the current system. This section will be completed after the benchmark is frozen and run.

---

## Files

| File | Contents |
|---|---|
| `source.md` | Full citation and source notes |
| `suite_public.json` | Public test suite (pending) |
| `results_public.json` | Public results (pending re-run) |
| `limitations.md` | Limitations specific to this incident test (pending) |
