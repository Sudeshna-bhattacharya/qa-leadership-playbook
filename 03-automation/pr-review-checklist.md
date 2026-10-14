# PR Review Checklist: Test Code

Reviewers tick what applies. Authors self-review against it before requesting a review.

## Value

- [ ] The test checks something that matters (linked to a story, risk or bug)
- [ ] It sits at the **right level**: could this be an API or unit test instead of UI?
- [ ] No duplication of coverage that already exists

## Correctness

- [ ] Assertions would **fail if the feature broke**. Try breaking it mentally (or actually).
- [ ] Negative and edge cases are covered where the risk is high
- [ ] Expected values are independent of the code under test, not copied from the response

## Reliability

- [ ] No hard waits (`waitForTimeout`, `sleep`)
- [ ] No order dependency between tests; unique test data; cleanup done
- [ ] Stable locators (role / label / test-id)
- [ ] Ran locally several times (`--repeat-each=5`) without flakiness

## Readability & maintainability

- [ ] Test name describes behaviour
- [ ] Follows [coding standards](coding-standards.md): naming, structure, tags
- [ ] Reuses existing fixtures and helpers instead of new copies
- [ ] No magic numbers or strings without explanation

## Hygiene

- [ ] No secrets, tokens or personal data
- [ ] No `.only`, no commented-out code
- [ ] Lint, type-check and CI are green
- [ ] Report and trace artefacts useful on failure

## Review etiquette

- Comment on the code, not the person. Ask questions ("What happens if…?").
- Label comments: **must**, **should**, or **nit**.
- Approve when it's better than before. Perfect can come in a follow-up.
