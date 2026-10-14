# QA in Agile

QA isn't a phase at the end of the sprint. It's a set of activities spread across the whole cycle.

## QA across the sprint

| When | QA activity | Output |
|---|---|---|
| **Backlog refinement** | Challenge ambiguity, ask "what if…", identify risks and test data needs | Testable acceptance criteria |
| **Three Amigos** (per story) | PO + Dev + QA agree behaviour with concrete examples | Examples in Given/When/Then |
| **Sprint planning** | Size testing and automation inside the story, not as a separate task | Realistic estimates |
| **Development** | Pair with devs on test design; review unit tests; prepare automation in parallel | Tests ready when code is |
| **PR / CI** | Automated checks run on every PR; QA reviews test code | Fast feedback |
| **Story testing** | Verify acceptance criteria, explore around them | Bugs found within the sprint |
| **Review / demo** | Show quality alongside features: new tests, risks found | Shared visibility |
| **Retro** | Bring data: escaped defects, flaky tests, blocked time | One quality improvement per sprint |

## Three Amigos: how I run them

**15 minutes, per story, before development starts.**

1. PO explains the *why* and the main rule.
2. Everyone writes examples, including the awkward ones:
   - *Given a basket with a discounted item, when the coupon is also applied, then…*
3. QA drives edge cases: empty, maximum, invalid, concurrent, permissions, failure of a dependency.
4. Disagreements become questions for the PO, not assumptions in code.
5. Examples go into the ticket and become the automated tests.

## Definition of Ready (story)

- [ ] User value and acceptance criteria are clear
- [ ] Examples agreed in Three Amigos
- [ ] Dependencies, test data and environments identified
- [ ] Non-functional needs stated (performance, accessibility, security)
- [ ] Small enough to finish and test within the sprint

## Definition of Done (story)

- [ ] Acceptance criteria verified
- [ ] Unit tests written; API/UI automation added at the [right level](../03-automation/automation-strategy.md)
- [ ] All CI checks green, no new flaky tests
- [ ] No open Sev 1 / Sev 2 defects for this story
- [ ] Accessibility checks pass (automated, plus keyboard check for UI changes)
- [ ] Code and test code reviewed
- [ ] Documentation / release notes updated where needed

## Exploratory testing: session-based

- **Charter:** *Explore [area] with [resources] to discover [information].*
  e.g. *Explore checkout payment failures with expired and declined test cards to discover how errors are communicated.*
- **Timebox:** 45–90 minutes
- **Debrief:** bugs raised, questions, ideas for new automated checks

## Bug bashes

Before major releases: 60 minutes, whole team, different personas and devices, a small prize for the most valuable find. It builds shared ownership of quality fast.
