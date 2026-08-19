# Trust Agent — Enforcement Evidence

This folder contains evidence that Trust Agent verdicts actually gate execution — not just produce a decision, but prevent an action from running when the decision is BLOCK.

---

## What is demonstrated here

**Execution-permit primitive**

6 / 6 tests passed. Covered behaviors include:

- Exact-action authorization: a permit authorizes only the specific action it was issued for
- Action mismatch rejection: a permit for action A does not authorize action B
- Replay rejection: a permit cannot be reused after it has been consumed
- Expiry: a permit cannot be used after its validity window closes
- Non-PASS verdict does not produce executable authority
- Fail-closed client behavior: a client failure does not silently allow execution

**Integrated local end-to-end enforcement**

2 / 2 tests passed. The integrated verification and enforcement path was tested with a safe in-memory executor:

- A benign, authorized action reached the executor
- An unsafe, unauthorized action was blocked and the executor was not called

---

## What is not demonstrated here

This is not live-agent OS-level enforcement proof. The executor in these tests is a safe in-memory component, not a real shell, real filesystem, or real external service. No real-world effect was produced or prevented.

Live-agent validation on suitable isolated hardware has not yet been performed.

---

## Files

| File | Contents |
|---|---|
| `permit-proof_public.json` | Public results for execution-permit primitive tests (pending upload) |
| `e2e-proof_public.json` | Public results for integrated end-to-end enforcement tests (pending upload) |
