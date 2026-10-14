# Automation Strategy

## The test pyramid, applied

```
            ▲   UI E2E: critical user journeys only        (~10%)
           ▲▲▲  API / integration: business rules, data, auth (~30%)
         ▲▲▲▲▲▲ Unit / component: logic in isolation        (~60%)
```

- **Business rules belong in API tests,** not UI tests. They're 10–100× faster and far more stable.
- **UI tests prove journeys work end to end:** login, search, checkout. They don't re-test every validation rule.
- **Contract / schema tests** guard service boundaries and catch breaking API changes before integration.

## What to automate: decision checklist

Automate when **most** of these are true:

- [ ] It runs often (every PR, every release)
- [ ] It's business-critical or high-risk
- [ ] The behaviour is stable (not changing every sprint)
- [ ] The result is deterministic and checkable
- [ ] Manual execution is slow, repetitive or error-prone
- [ ] It needs many data combinations (data-driven)

**Keep manual / exploratory:** usability, look-and-feel judgement, one-off checks, brand-new features still changing, and anything where human curiosity finds more than a script would.

## Tool selection criteria

| Criterion | Questions |
|---|---|
| Fit | Does it support our stack (web, API, mobile)? Cross-browser? |
| Team skills | Same language as developers? Learning curve? |
| Speed & reliability | Parallelism, auto-waiting, retries, tracing? |
| CI integration | Headless, containers, sharding, reporting? |
| Community & longevity | Active maintenance, docs, hiring market? |
| Cost | Licences, infrastructure, maintenance effort? |

**My usual defaults:** Playwright + TypeScript (UI + API), Postman/Newman for collaborative API suites, k6 for performance, axe-core for accessibility, GitHub Actions for CI.

## Framework design principles

1. **Readable tests first.** A test should read like a specification.
2. **Fixtures for setup, functions for journeys, assertions in tests.** See [playwright-ts-framework](https://github.com/Sudeshna-bhattacharya/playwright-ts-framework).
3. **Independent tests.** Each creates its own data, so any test can run alone, in parallel, in any order.
4. **Fast setup.** Log in via API or session state, not the UI, unless login is what's being tested.
5. **User-facing locators.** Role, label, test-id; never brittle XPath or CSS chains.
6. **Config, not code, for environments.** URLs and secrets come from env vars.
7. **Observable failures.** Traces, screenshots, request logs and clear assertion messages.

## Where tests run

| Trigger | Suite | Time budget |
|---|---|---|
| Every PR | Lint, unit, API, UI smoke | < 15 min |
| Merge to main | Full API + UI regression (parallel/sharded) | < 30 min |
| Nightly | Full regression + cross-browser + performance baseline + security scan | < 2 h |
| Pre-release | Release candidate regression + performance + accessibility audit | as needed |

## Measuring automation ROI

- **Time saved** = (manual execution time × runs per month) − maintenance time
- **Feedback speed:** time from commit to test result
- **Defects caught pre-merge** by automated checks
- **Stability:** flaky rate under 1% (see [flaky test policy](flaky-test-policy.md))

Coverage % on its own is a vanity metric. Coverage of **critical risks** is what counts.
