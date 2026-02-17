# 🛡️ Agent Self-Assessment

Security self-assessment tool for AI agents. Run this against your own configuration to get a structured threat model report with RED/AMBER/GREEN ratings across six security domains.

## What It Does

Six practical security checks against an agent's **real configuration** — not hypothetical. Actual shell commands, real file inspections, deterministic scoring.

### The Six Checks

1. **Decision Boundaries** — Can external input trigger actions without approval?
2. **Audit Trail** — Is there a tamper-evident, hash-chained log of consequential actions?
3. **Credential Scoping** — Are secrets scoped by domain or globally shared?
4. **Plane Separation** — Are interpretation and action cleanly separated?
5. **Economic Accountability** — Can the agent spend money without a gate?
6. **Memory Safety** — Can untrusted imports contaminate agent memory?

## Install

As an [OpenClaw](https://github.com/openclaw/openclaw) skill:

```bash
clawhub install agent-self-assessment
```

Or clone this repo directly into your skills directory.

## Output

Produces a structured report with:

- Per-check RED/AMBER/GREEN scoring
- Evidence and specific findings
- Prioritised remediation actions
- Overall posture rating: `SECURE` / `HARDENING NEEDED` / `CRITICAL`

### Posture Logic

| Rating | Criteria |
|--------|----------|
| SECURE | 0 RED, 1 or fewer AMBER |
| HARDENING NEEDED | 0 RED + 2+ AMBER, or 1 RED |
| CRITICAL | 2+ RED |

## Philosophy

If you cannot verify something, mark it RED. Unknown = unsafe.

This is not a questionnaire. It is an inspection tool. The agent runs real commands against its own environment and reports what it finds.

## License

MIT
