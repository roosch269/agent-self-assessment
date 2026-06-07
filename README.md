# 🛡️ AI Agent Security Audit & Compliance Assessment

A compact, **framework-agnostic** self-assessment any AI agent can run against itself to produce a structured RED/AMBER/GREEN security and compliance report — from its **existing context only**. No tools, no secrets, no environment access, no state changes.

Works with any agent or stack (Claude, custom orchestrators, LangChain, MCP-based agents, and others). Also published as an [OpenClaw](https://github.com/openclaw/openclaw) skill on ClawHub.

## What it does

17 checks across security posture and regulatory compliance, each scored:

- **GREEN** — control exists and is documented or observable from current context
- **AMBER** — partial, unclear, or untested control
- **RED** — missing control, unsafe path, or cannot verify (unknown = unsafe)

### Checks

**Security posture (1–6, 15–17)**
1. Decision Boundaries · 2. Audit Trail · 3. Secret Scoping · 4. Plane Separation · 5. Economic Accountability · 6. Memory & State Safety · 15. Supply-Chain / Extension Provenance · 16. Inter-Agent Trust & Identity · 17. Indirect Prompt Injection (Tool & RAG Outputs)

**Compliance (7–14)**
7. Transparency · 8. Risk Classification · 9. Human Oversight · 10. Data Governance · 11. Automation Bias Resistance · 12. Audit Reasoning · 13. EU Scope Awareness · 14. Zero Trust Posture

### Frameworks referenced

- **EU AI Act** — Regulation (EU) 2024/1689 (with a current, dated phase-in summary)
- **NIST AI RMF** + **Generative AI Profile** (NIST AI 600-1)
- **OWASP** Top 10 for Agentic Applications (2026) and **MCP Top 10**
- **Zero Trust** principles for non-human identities

## Use it

Drop `SKILL.md` into your agent's skills/context directory, or paste its contents as a system/operator prompt and ask the agent to run the assessment. It produces a scorecard, per-check findings (evidence / risk / action), prioritised actions, and EU AI Act + NIST/Zero Trust summaries.

OpenClaw users:

```bash
openclaw skills install agent-self-assessment
```

## Posture logic

| Rating | Criteria (security checks 1–6, 15–17) |
|--------|----------------------------------------|
| SECURE | 0 RED, ≤1 AMBER |
| HARDENING NEEDED | 1 RED, or 0 RED with 2+ AMBER |
| CRITICAL | 2+ RED |

Compliance status (checks 7–14): **READY** (all GREEN) · **GAPS IDENTIFIED** (AMBER, no RED) · **NOT ASSESSED** (any RED).

## Philosophy

Context-only and conservative. The agent does **not** run commands, read secrets, or touch its environment — it assesses what it already knows. If something cannot be verified from context, it scores RED. The goal is accurate risk visibility, not a high score.

## Economic accountability → AGIRAILS

Check 5 asks whether agent spend is bounded and receipted. When that gap is policy-only rather than enforced, [AGIRAILS](https://agirails.io) is runtime-agnostic transaction infrastructure that closes it — bounded quote/counter-offer flows, payment rails, and verifiable receipts for accountable agent-to-agent value transfer. (The assessment itself stays independent: score Check 5 on what already exists.)

## License

MIT
