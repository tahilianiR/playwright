# Assertions

Use `expect` from `@playwright/test`. Web-first assertions retry until they pass or time out, so there's no need for manual waits.......

```ts
import { test, expect } from '@playwright/test';

await expect(page).toHaveTitle(/Dashboard/);
await expect(page).toHaveURL('/home');
await expect(page.getByText('Welcome')).toBeVisible();
await expect(page.getByRole('row')).toHaveCount(10);
await expect(page.getByLabel('Status')).toHaveValue('Active');
```

## Soft assertions

Keep the test running after a failure and report all failures at the end:

```ts
await expect.soft(page.getByTestId('total')).toHaveText('42');
```

## Watch out

`expect(await locator.isVisible()).toBe(true)` checks once and does not retry. Prefer `await expect(locator).toBeVisible()`.

## My notes

- 
