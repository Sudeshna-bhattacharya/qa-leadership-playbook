# Manual → Automation Upskilling Plan (12 weeks)

Manual testers already have the hardest skill: knowing **what** to test. This programme adds the **how** without losing that judgement.

**Format:** ~6 hours a week protected time · weekly 1:1 pairing with a mentor · real work from week 5 onward
**Stack:** TypeScript · Postman · Playwright · Git · GitHub Actions

## Phase 1: Foundations (weeks 1–4)

| Week | Topic | Practical exercise |
|---|---|---|
| 1 | Git & GitHub basics: clone, branch, commit, PR | Open a PR fixing a typo in test docs |
| 2 | JavaScript/TypeScript essentials: variables, functions, arrays, objects, async/await | 10 small coding katas |
| 3 | HTTP & APIs: methods, status codes, headers, JSON, auth | Explore a public API in Postman |
| 4 | Postman scripting: tests, variables, chaining | Build a chained CRUD collection with assertions |

**Checkpoint:** a Postman collection with chained requests and negative tests, reviewed by the mentor.

## Phase 2: Automation core (weeks 5–8)

| Week | Topic | Practical exercise |
|---|---|---|
| 5 | Playwright basics: locators, actions, web-first assertions | Automate 3 existing manual test cases |
| 6 | Framework structure: fixtures, helpers, test data | Refactor own tests to use shared fixtures |
| 7 | API testing in Playwright, schema validation | Add API tests for a real team story |
| 8 | Debugging: traces, UI mode, reading CI failures | Fix a real flaky or failing test |

**Checkpoint:** first automation PR merged into the team's real suite.

## Phase 3: Independence (weeks 9–12)

| Week | Topic | Practical exercise |
|---|---|---|
| 9 | CI/CD: pipelines, tags, parallel runs, reports | Add a tagged suite to the pipeline |
| 10 | Data-driven tests & test design for automation | Convert a repetitive manual area into data-driven tests |
| 11 | Code review: giving and receiving | Review 3 PRs using the [checklist](../03-automation/pr-review-checklist.md) |
| 12 | Capstone | Automate a full feature (API + UI) for a live story, then demo it to the team |

## Principles that make it work

- **Protected time is non-negotiable.** Without it, the plan stalls by week 3.
- **Real work early.** Exercises on our own product keep motivation high.
- **Pair, don't lecture.** Mentors work alongside; learners drive the keyboard.
- **Celebrate milestones.** First merged PR, first bug caught by own automation, capstone demo.
- **Keep the tester mindset.** Automation serves test design, not the other way round.

## Measuring success

- PRs merged per learner (trend, not target)
- Share of the learner's stories delivered with automation
- Confidence self-rating at weeks 0, 6 and 12
- Learner progression on the [skills matrix](skills-matrix.md)
