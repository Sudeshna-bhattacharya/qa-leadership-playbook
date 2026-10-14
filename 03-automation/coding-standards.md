# Automation Coding Standards

Test code is production code. It is reviewed, linted and maintained with the same care.

## Naming

| Item | Convention | Example |
|---|---|---|
| Spec files | `<feature>.spec.ts` | `checkout.spec.ts` |
| Test names | Behaviour in plain English, no "test" prefix | `customer can complete a purchase with a saved card` |
| Describe blocks | Feature or capability | `describe('Checkout')` |
| Helpers | Verb-first | `addToCart()`, `createBooking()` |
| Test data builders | `build<Thing>()` | `buildCustomer({ country: 'UK' })` |

## Structure: Arrange, Act, Assert

```ts
test('locked-out user sees an error', async ({ page }) => {
  // Arrange
  const user = users.lockedOut;
  // Act
  await login(page, user);
  // Assert
  await expect(page.getByTestId('error')).toContainText('locked out');
});
```

- One behaviour per test. Several assertions about that behaviour are fine.
- Use `test.step()` to label phases of long journeys. They show up in reports.

## Rules

1. **No hard waits.** Never `waitForTimeout(3000)`. Wait for a condition: web-first assertions, `waitForResponse`, polling.
2. **User-facing locators** in this order: `getByRole` → `getByLabel` → `getByTestId` → text. No XPath.
3. **Independent and parallel-safe.** No shared mutable state; unique data per test; clean up what you create.
4. **No secrets in code.** Use environment variables or a secret store, with `.env.example` committed.
5. **Assertions in tests, not in helpers.** Helpers do things; tests decide what's correct. *Exception:* helpers that validate contracts, such as `parseBody(res, Schema)`.
6. **Meaningful failure messages.** `expect(total, 'cart total after coupon').toBe(90)`
7. **Tag tests** for selection: `@smoke`, `@regression`, plus feature tags.
8. **No commented-out tests.** Skip with a reason and a ticket: `test.skip(true, 'BUG-123: payment sandbox down')`
9. **Data-driven over copy-paste.** One test definition, a table of cases.
10. **Lint and format in CI.** ESLint (with the Playwright plugin) and Prettier. Warnings are fixed, not ignored.

## Folder layout (Playwright example)

```
src/
  api/        thin typed API clients
  data/       personas, static data, builders
  fixtures/   setup & teardown as fixtures
  ui/         reusable user journeys (functions)
  schemas/    response contracts
tests/
  api/  ui/
```
