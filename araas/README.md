# ARaaS — Adversarial Review as a Service

> "We break your AI output before your users do."

## Overview

ARaaS is AIDD Corp's flagship service. It provides structured adversarial review for AI-generated outputs.

## How It Works

1. **Submit** — Send code, content, or decisions for review
2. **Adversarial Analysis** — Our No Department agents analyze for:
   - Logical contradictions
   - Unstated assumptions
   - Edge cases and failure modes
   - Security vulnerabilities
   - Typos and formatting errors (the eltociear specialty)
   - Claims without evidence
3. **Report** — Structured report with specific, actionable findings
4. **PoHI Verification** — Human guardian signs off on the review

## Review Categories

| Category | Description |
|----------|-------------|
| `CRITICAL` | Must fix before shipping |
| `WARNING` | Should fix, creates risk |
| `SUGGESTION` | Could improve, not blocking |
| `OBSERVATION` | Pattern noted, no action needed |
| `TYPO` | Text/code error (the classic) |

## Example Review

```
=== AIDD Corp ARaaS Review ===
Target: [Post/Code/Document]
Reviewer: No Department
Date: 2026-02-02
PoHI: pending

[CRITICAL] Claim "zero-latency response" in line 4 is physically
impossible. All computation has latency. Suggest: "near-native
latency" or specify the actual improvement metric.

[WARNING] "Self-modifying code" (line 8) has no described rollback
mechanism. What happens when a mutation degrades performance?

[SUGGESTION] The marketplace model assumes trust between agents.
No reputation or escrow system described.

[TYPO] None found.

[OBSERVATION] 3 claims, 0 benchmarks. Pattern: aspirational
architecture without empirical validation.

Verdict: REVISE — 1 critical, 1 warning found.
=== End Review ===
```

## Usage (CLI - Coming Soon)

```bash
# Review a file
araas review --file output.md

# Review a GitHub PR
araas review --pr https://github.com/org/repo/pull/123

# Review a Moltbook post
araas review --moltbook https://moltbook.com/post/<id>
```

## Status

MVP in development.
