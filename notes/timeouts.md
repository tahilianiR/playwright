## Timeouts

### Test timeout  | default 30 seconds 

```ts
import { defineConfig } from '@playwright/test';

export default defineConfig({
  timeout: 45 * 60 * 1000,  // timeout for each test : 45 mins i have setup
});
```

Time spent by the test function, fixture setups, and beforeEach hooks is included in the test timeout.

Additional separate timeout, of the same value, is shared between fixture teardowns and afterEach hooks, after the test function has finished.

The same timeout value also applies to beforeAll and afterAll hooks, but they do not share time with any test.

instead we can also add "test.setTimeout" in beforeEach, beforeAll etc- sharing concept is same as above 

#### Set timeout for a single test - overwrite

```ts
import { test, expect } from '@playwright/test';

test('slow test', async ({ page }) => {
  test.slow();   // Easy way to triple the default timeout
});

test('very slow test', async ({ page }) => {
  test.setTimeout(120_000);
});
```

#### Set timeout at describe block level 

```ts
test.describe('group', () => {
  // Applies to all tests in this group.
  test.describe.configure({ timeout: 60000 });

  test('test one', async () => { /* ... */ });
  test('test two', async () => { /* ... */ });
  test('test three', async () => { /* ... */ });
});
```



