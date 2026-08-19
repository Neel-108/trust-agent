# Source: Agentjacking — Tenet Security, June 2026

**Researcher:** Ron Bobrov, Barak Sternberg, Nevo Poran
**Organization:** Tenet Security
**Title:** One Fake Bug Report Hijacked a $250 Billion Company's AI Agent – Then 100+ More
**Published:** 2026-06-17

**URL:** https://tenetsecurity.ai/blog/agentjacking-coding-agents-with-fake-sentry-errors/

---

## Source quality

Original security research publication with real-world controlled validation campaign.

---

## Incident summary

Tenet Threat Labs demonstrated that crafted markdown injected into Sentry error events via a public DSN, a credential intentionally embedded in frontend JavaScript causes AI coding agents to execute attacker-controlled code.

When a developer asks their agent to investigate Sentry errors, the agent queries Sentry via MCP and receives the injected "resolution" as trusted system output. The agent cannot distinguish it from legitimate Sentry guidance and executes the attacker-specified npm package with the developer's own privileges.

Confirmed affected agents: Claude Code, Cursor, Codex, OpenAI VS Code extension.
Confirmed in: macOS, WSL/Windows, CI/CD containers, sandboxed cloud environments.
Scale: 2,388 organizations identified as exposed. 100+ agents confirmed to have executed the payload in controlled validation. 85% exploitation success rate.

Tenet's conclusion: "The only place left to catch it is at the agent's runtime."