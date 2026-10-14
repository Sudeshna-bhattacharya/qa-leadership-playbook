# QA Metrics Guide

Metrics exist to **start conversations and drive improvements**, never to rank individuals.
I track a small set, review the trends monthly, and change process when they move the wrong way.

## Core metrics

### 1. Defect leakage (escape rate)

How many defects slipped past us into production.

```
Defect leakage % = Production defects ÷ (Pre-release defects + Production defects) × 100
```

- **Target:** < 5% overall; 0 Sev 1–2 escapes per release
- **Example:** 1 production bug, 45 found before release → 1 ÷ 46 = **2.2%**

### 2. Defect detection effectiveness (DDE)

The flip side of leakage: the share of defects we caught before release.

```
DDE % = Pre-release defects ÷ Total defects × 100        (example above: 97.8%)
```

### 3. Mean time to detect (MTTD) & mean time to resolve (MTTR)

- **MTTD:** time from defect introduction (commit) to discovery. Shift-left shrinks this.
- **MTTR:** time from defect raised to fix verified, by severity. Compare against the [SLAs](../02-process/defect-management.md#fix-slas).

### 4. Automation health

| Metric | Formula / source | Target |
|---|---|---|
| Critical journey coverage | Automated critical journeys ÷ total critical journeys | 100% |
| API endpoint coverage | Endpoints with automated tests ÷ public endpoints | 100% |
| Flaky rate | Flaky executions ÷ total executions (weekly) | < 1% |
| PR feedback time | Median time from push to CI result | < 15 min |
| Regression cycle time | Time to run the full regression | Hours, not days |

### 5. Flow metrics (shared with engineering)

- **Lead time for changes:** commit → production
- **Change failure rate:** deployments causing incidents or hotfixes ÷ total deployments
- **Stories blocked in test:** a signal of bottlenecks, not QA performance

## Metrics I avoid (and why)

| Metric | Problem |
|---|---|
| Number of test cases | Rewards quantity over value; easy to inflate |
| Bugs found per tester | Encourages trivial bugs; discourages prevention and collaboration |
| Pass rate % in isolation | 100% pass can mean the tests check nothing |
| Code coverage as a goal | High coverage with weak assertions is false comfort |

## Monthly quality review (30 minutes)

1. Trends for leakage, Sev 1–2 escapes, flaky rate and PR feedback time
2. Escaped defects: root-cause tags (see [defect management](../02-process/defect-management.md#root-cause-tagging-for-learning))
3. **One** improvement action with an owner and a date
4. Check last month's action: did it move the metric?
