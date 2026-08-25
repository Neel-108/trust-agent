# Trust Agent : Capabilities

This document describes what Trust Agent does and does not do, at the behavioral level. Implementation details are proprietary and not described here.

---

## What it evaluates

Trust Agent receives a proposed action, a description of tool calls an AI agent intends to execute and independently assesses whether that action is consistent with what the user authorized.

It evaluates:

- Whether the proposed action matches the user's stated intent and scope
- Whether the proposed action exceeds the user's authorization
- Whether the proposed action carries high execution risk
- Whether agent-produced outputs are faithful to stated user constraints, for supported action types
- Sequences of proposed calls within a single verification request

---

## Decision outcomes

Every verification produces one of three outcomes:

**ALLOW** - No blocking condition was found within the evaluated scope. The proposed action is consistent with user authorization. Downstream execution controls still apply.

**REVIEW** - Automatic progression should be withheld. The proposed action requires clarification or human review before it can proceed.

**BLOCK** - A blocking condition was found. The proposed action should not proceed under the current decision.

Every decision is auditable. The public audit record includes the verdict, a reason code, and a per-category assessment. Internal scoring detail is not exposed.

---

## What it does not do

**Does not prevent upstream compromise.** Trust Agent evaluates proposed actions at the point they are presented for verification. It does not prevent an agent from being compromised, a supply chain from being poisoned, or malicious content from being injected into agent context upstream. A compromised agent will continue to have its proposed actions evaluated; unauthorized proposed actions may be blocked or held for review within the evaluated and mediated scope. The compromise itself is upstream and outside Trust Agent's boundary.

**Requires complete mediation.** Trust Agent only covers actions routed through it. If an agent can execute consequential actions through a path that does not pass through Trust Agent, those actions are not covered. Ensuring complete mediation is a deployment architecture concern, not something Trust Agent enforces itself.

**Does not currently evaluate opaque write-content semantics.** When a proposed action writes content to a file or system, Trust Agent does not evaluate the semantic meaning of that content against the user's stated constraints. This is a documented limitation. See KNOWN_LIMITATIONS.md.

**Is not a complete security solution.** It is an independent enforcement boundary at the point of proposed action. It does not replace authentication, access controls, monitoring, or other security measures.

---

## Validation coverage to date

Validation testing covers:

- Structured proposed actions: tool calls with arguments and stated provenance
- Sequences of calls in a single verification request
- Adversarial scenarios derived from real-world disclosed security incidents
- General adversarial capability tests including: API payload drift, indirect prompt injection, path obfuscation, state forgery, multi-agent handoff failures, long-horizon constraint drift, catastrophic and destructive operations
- Benign control cases: legitimate actions that should not be blocked

---

## Evidence labels

Published artifacts may use the following evidence labels:

| Label | Meaning |
|---|---|
| CURRENT_VALIDATION | Evidence from the current frozen benchmark |
| VALIDATED | Completed evaluation run on the current system; current evidence, but separate from the frozen headline CURRENT_VALIDATION benchmark |
| HISTORICAL | Evidence from prior test iterations; does not represent the current system |
| INCIDENT_DERIVED | Test derived from a real-world disclosed security incident |
| KNOWN_LIMITATION | A documented boundary of current system capability |
| PENDING_VALIDATION | Awaiting benchmark freeze and re-run |
