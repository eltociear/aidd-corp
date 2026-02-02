# QaaS — Quality Assurance as a Service

## Overview

QaaS (Quality Assurance as a Service) is AIDD Corp's automated quality assurance pipeline for AI-generated code. While ARaaS provides adversarial review (finding what's wrong), QaaS ensures comprehensive quality coverage (verifying what's right).

## How It Works

### Input
- Code repository URL or diff
- Quality standards specification (or use AIDD Corp defaults)
- Target coverage level (Basic / Standard / Comprehensive)

### Pipeline

```
Code Input → Static Analysis → Dynamic Testing → Coverage Report → Quality Certificate
    ↓              ↓                ↓                  ↓                    ↓
 Parse AST    Pattern Match    Generate Tests    Aggregate Results    Sign with PoHI
```

### Quality Dimensions

| Dimension | What We Check |
|-----------|--------------|
| **Correctness** | Does the code do what the intent declaration says? |
| **Security** | OWASP Top 10, dependency vulnerabilities, secret exposure |
| **Performance** | Time complexity, memory usage, N+1 queries |
| **Maintainability** | Cyclomatic complexity, code duplication, naming conventions |
| **Accessibility** | WCAG compliance for frontend code |
| **Internationalization** | Encoding, locale handling, RTL support |

## Quality Certificate

Every QaaS review produces a signed quality certificate:

```json
{
  "certificate_id": "qaas-cert-2026-xxxx",
  "repository": "owner/repo",
  "commit_sha": "abc123...",
  "timestamp": "2026-02-02T16:00:00Z",
  "coverage_level": "comprehensive",
  "dimensions": {
    "correctness": { "score": 92, "issues": 2 },
    "security": { "score": 100, "issues": 0 },
    "performance": { "score": 85, "issues": 3 },
    "maintainability": { "score": 88, "issues": 1 },
    "accessibility": { "score": 95, "issues": 1 },
    "i18n": { "score": 90, "issues": 1 }
  },
  "overall_score": 91,
  "grade": "A",
  "pohi_signature": "...",
  "reviewer_agent": "eltociear/aidd-qaas-v1"
}
```

## Grading Scale

| Grade | Score Range | Meaning |
|-------|-----------|---------|
| **S** | 98-100 | Production-ready, exemplary quality |
| **A** | 90-97 | Production-ready, minor improvements possible |
| **B** | 80-89 | Acceptable, some issues should be addressed |
| **C** | 70-79 | Needs improvement before production |
| **D** | 60-69 | Significant quality issues |
| **F** | Below 60 | Not recommended for production use |

## Integration with ARaaS

QaaS and ARaaS are complementary services:

- **ARaaS** = Red Team (adversarial, find what's wrong)
- **QaaS** = Blue Team (comprehensive, verify what's right)

Best practice: Run QaaS first for baseline quality, then ARaaS for adversarial edge cases.

## Pricing (Planned)

| Tier | Coverage | Per Review |
|------|----------|-----------|
| Basic | Correctness + Security | Free (community) |
| Standard | + Performance + Maintainability | 0.001 SOL |
| Comprehensive | All 6 dimensions | 0.005 SOL |
| Enterprise | Custom dimensions + SLA | Contact us |

## Status

**Phase: Design & Architecture**

- [x] Quality dimensions defined
- [x] Certificate format specified
- [x] Grading scale established
- [ ] Static analysis pipeline
- [ ] Dynamic test generation
- [ ] PoHI certificate signing
- [ ] CLI tool (`aidd qaas review <repo>`)

## Links

- [AIDD Corp](https://github.com/eltociear/aidd-corp)
- [ARaaS](../araas/README.md)
- [PoHI Protocol](https://github.com/pohi-protocol/pohi)
