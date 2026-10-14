# Risk-Based Testing

There's never time to test everything equally. Risk-based testing makes the trade-off **explicit and agreed** instead of accidental.

## 1. Score each area

**Risk score = Impact × Likelihood** (each 1–5)

### Impact: what happens if this fails in production?

| Score | Meaning | Examples |
|---|---|---|
| 5 | Money, data or legal exposure; core flow blocked | Payments, auth, data loss, compliance |
| 4 | Major feature unusable for many users | Search, checkout step, onboarding |
| 3 | Feature degraded, workaround exists | Filters, exports |
| 2 | Minor inconvenience | Cosmetic issues on secondary pages |
| 1 | Negligible | Internal-only text |

### Likelihood: how likely is it to break?

| Score | Signals |
|---|---|
| 5 | New code, complex logic, many integrations, unclear requirements |
| 4 | Significant change to existing code; history of defects here |
| 3 | Moderate change; some test coverage exists |
| 2 | Small change; well covered by automation |
| 1 | Untouched, stable, fully covered |

## 2. Map score to test depth

| Score | Level | What we do |
|---|---|---|
| **15–25** | 🔴 High | API + UI automation, negative and edge cases, exploratory sessions, performance and security checks, peer review of test design |
| **8–14** | 🟠 Medium | Automation for main flows and key negatives, one exploratory session |
| **1–7** | 🟢 Low | Smoke coverage, rely on existing regression, spot checks |

## 3. Run it as a team exercise

1. In refinement or release planning, list the areas that are changing.
2. Score them together: Product (impact), developers (likelihood), QA (facilitates and challenges).
3. Record the table in the [test plan](test-plan-template.md).
4. Revisit when scope changes or defects cluster somewhere unexpected.

## 4. Why it works

- Product owners **see and accept** what gets less testing.
- Test effort follows **business value**, not whoever shouts loudest.
- It gives a defensible answer to "why didn't we test X?"
