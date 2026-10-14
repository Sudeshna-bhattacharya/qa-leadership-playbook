# Flaky Test Policy

A flaky test passes and fails on the same code. Left alone, flaky tests teach the team to ignore red builds, and that's how real bugs ship.

**Target:** flaky rate **< 1%** of test executions per week.

## The process

```
Detect → Quarantine (same day) → Diagnose → Fix → Restore → Learn
```

### 1. Detect

- CI retries are allowed (max 2) **only to detect flakiness, not to hide it.** A test that passes on retry is reported as *flaky*.
- A weekly flaky report lists tests by flaky count (from Playwright/Allure retry data).

### 2. Quarantine

- Tag the test `@quarantine` and exclude it from the blocking PR suite. It still runs nightly in a non-blocking job.
- Raise a ticket with the failure evidence (trace, logs, screenshot).
- **Owner assigned and fix target: 5 working days.**

### 3. Diagnose: common causes

| Symptom | Likely cause | Fix |
|---|---|---|
| Element not found / timeout intermittently | Race with rendering or network | Web-first assertions; wait for the specific response |
| Passes alone, fails in parallel | Shared data or state | Unique data per test; isolate accounts |
| Fails at certain times | Dates, time zones, caching | Freeze or control time; build dates relative to "now" |
| Fails only in CI | Resource limits, environment config | Match CI locally (container); check headless differences |
| Random data breaks it | Unconstrained generators | Constrain data, log the seed |
| Third-party slowness | External dependency | Mock or stub at the boundary; contract-test separately |

### 4. Fix and restore

- Prove the fix: run with `--repeat-each=20` locally and in CI.
- Remove the `@quarantine` tag and close the ticket with the root cause.

### 5. Learn

- If a test stays quarantined for **more than 2 sprints**, delete it or rewrite it at a lower level. A permanently quarantined test is dead weight.
- Review flaky root causes in retro and update the [coding standards](coding-standards.md) when a pattern repeats.
