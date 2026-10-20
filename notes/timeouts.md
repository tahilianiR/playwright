## Timeouts


```ts
export default defineConfig({
  globalTimeout: 4 * 60 * 60 * 1000, 
  timeout: 30 * 60 * 1000, 

  expect: { timeout: 20 * 1000 }, 
  
  use: {
    actionTimeout: 20 * 1000, 
    navigationTimeout: 60 * 1000,
  },
});
````

### 1. Global timeout __ default no timeout | globalTimeout: 4 * 60 * 60 * 1000 



### 2. Test timeout __ default 30 seconds | timeout: 20 * 60 * 1000 | test.setTimeout(ms) 

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


### 3. expect timeout  __ default 5 seconds |  expect: { timeout: } | assertion level

```ts
import { defineConfig } from '@playwright/test';

export default defineConfig({
  expect: {
    timeout: 10_000,
  },
});
```

#### Specify expect timeout for a single assertion
```ts
import { test, expect } from '@playwright/test';

test('example', async ({ page }) => {
  await expect(locator).toHaveText('hello', { timeout: 10_000 });
});
```



### 4. Action timeout __ default no timeout | use: { actionTimeout: 10_000 }  | locator.click({ timeout: 10_000 })


### 5. Navigation  timeout __ default no timeout | use: { navigationTimeout: 30_000 } | page.goto('/', { timeout: 30_000 })


### Fixture  timeout __ later....

### Notes
* A good follow-up point: action and navigation timeouts have no limit by default, but they are still bounded by the test timeout. If the test times out first, the action fails with it.