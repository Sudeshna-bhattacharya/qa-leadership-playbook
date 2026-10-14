# AI-Assisted Testing Guidelines

AI makes testers faster. It doesn't replace their judgement. These guidelines set out where AI helps, where it doesn't, and the rules that keep quality and data safe.

## Where AI helps

| Use case | How | Human responsibility |
|---|---|---|
| **Test idea generation** | Give the story and acceptance criteria; ask for edge cases, negative paths and risks | Prune, prioritise, add domain knowledge |
| **Test data** | Generate realistic, varied data (names with accents, boundary values, invalid formats) | Make sure no real personal data is used |
| **Automation code** | Draft tests, fixtures, schema definitions, refactors | Review like any PR; run it; check that the assertions actually assert |
| **Failure triage** | Summarise logs, traces and stack traces; suggest likely causes | Confirm the root cause before acting |
| **Bug reports** | Turn rough notes into clear repro steps | Verify steps reproduce exactly |
| **Documentation** | Draft test plans, release notes, READMEs | Correct facts and context |
| **Exploratory charters** | Suggest charters for a feature | Choose and run the sessions; humans explore |

## Where AI is not the answer

- Deciding **what matters** to the business (risk and priority stay human decisions)
- Signing off a release
- Accessibility judgements that need real assistive-technology testing
- Anything requiring access to production or customer data

## Guardrails

1. **No sensitive data in prompts.** No customer data, credentials, tokens, internal URLs or proprietary code unless the tool is approved for it by the organisation.
2. **Use approved tools only,** in line with company policy.
3. **Every AI output is a draft.** It is reviewed by a person who understands it.
4. **Tests must fail for the right reason.** Break the feature, or invert the assertion, to prove an AI-written test can fail.
5. **Don't let AI "fix" tests by weakening assertions.** A green build from a loosened assertion is a hidden defect.
6. **Be transparent.** Note significant AI assistance in PR descriptions where the team asks for it.

## Prompt patterns that work

**Edge cases from a story**

> You are a senior QA engineer. Here is a user story and its acceptance criteria: […]. List edge cases, negative scenarios and risks grouped by: input validation, state, permissions, concurrency, integrations, accessibility. Flag anything ambiguous as a question for the product owner.

**Draft an automated test**

> Using Playwright + TypeScript with our conventions (fixtures for setup, user-facing locators, no hard waits, assertions in the test), write a test for: […]. Use `getByRole`/`getByTestId`. Explain each assertion.

**Triage a failure**

> Here is a failing test, its error and trace summary: […]. List the 3 most likely causes in order of likelihood, how to confirm each, and whether it looks like a product bug, test bug or environment issue.

## Testing AI features (when the product itself uses AI)

- Test **behaviour ranges, not exact strings.** Check structure, constraints, tone and safety rules.
- Build **evaluation sets** of representative and adversarial inputs; track pass rates over model or prompt changes.
- Check guardrails: prompt injection, harmful content, data leakage, refusal behaviour.
- Monitor in production: user feedback, flagged responses, drift.
