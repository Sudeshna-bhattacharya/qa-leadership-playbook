# Defect Management

## Severity vs priority

**Severity** = technical impact (set by QA). **Priority** = business urgency (set by Product). They are often different.

### Severity

| Level | Definition | Example |
|---|---|---|
| **Sev 1: Critical** | System down, data loss or corruption, security breach, core flow blocked for all users, no workaround | Checkout fails for every user |
| **Sev 2: Major** | Major feature broken or wrong results for many users; workaround is painful | Wrong tax calculated on orders |
| **Sev 3: Moderate** | Feature partly broken; reasonable workaround exists | Filter resets after pagination |
| **Sev 4: Minor** | Cosmetic or low-impact issue | Misaligned icon, typo |

### Priority

| Level | Meaning |
|---|---|
| **P1** | Fix immediately (hotfix) |
| **P2** | Fix in current sprint / before release |
| **P3** | Schedule in upcoming sprints |
| **P4** | Backlog: fix when convenient |

**Examples of the difference:**

- Typo in the company name on the home page → **Sev 4, P1** (brand impact)
- Crash in an admin report used once a year → **Sev 2, P3**

## Fix SLAs

| Severity | Acknowledge | Fix target |
|---|---|---|
| Sev 1 | 30 min | Hotfix within 24 h |
| Sev 2 | 4 h | Within current sprint / before release |
| Sev 3 | 2 days | Prioritised in next 2 sprints |
| Sev 4 | 1 week | Backlog, reviewed monthly |

## Bug lifecycle

```
New → Triaged → In Progress → In Review → Ready for Test → Verified → Closed
          │                                      │
          ├─→ Won't Fix / Duplicate / Not a Bug   └─→ Reopened → In Progress
          └─→ Deferred (with reason + review date)
```

## Triage

- **When:** daily, 15 minutes (during release hardening); twice a week otherwise
- **Who:** QA Lead, Product Owner, a Tech Lead
- **Agenda:** new bugs → confirm severity, set priority, assign owner; review reopened and aged bugs

## A good bug report

Use the [bug report issue form](../.github/ISSUE_TEMPLATE/bug_report.yml). The essentials:

1. **Title:** *[Area] What's wrong, under which condition*, e.g. *[Checkout] Total ignores coupon when basket has a discounted item*
2. **Environment & build** (URL, version, browser/device)
3. **Steps to reproduce:** numbered, minimal, with test data
4. **Expected vs actual**
5. **Evidence:** screenshot, video, trace, HAR, logs, request id
6. **Severity** (and suggested priority)
7. **Frequency:** always / intermittent (x of y attempts)

## Root-cause tagging for learning

Every Sev 1–2 and every escaped defect gets a root-cause tag:
`requirements` · `design` · `code` · `test gap` · `environment/config` · `third party` · `data`

Reviewed monthly. Patterns drive process changes (e.g. many `requirements` → stronger Three Amigos).
