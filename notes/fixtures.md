# Fixtures

Fixtures are what you receive in the test function: `page`, `context`, `browser`, `request`. Each test gets fresh ones, so tests stay isolated.

## Custom fixture

```ts
import { test as base } from '@playwright/test';
import { LoginPage } from './pages/login-page';

type MyFixtures = { loginPage: LoginPage };

export const test = base.extend<MyFixtures>({
  loginPage: async ({ page }, use) => {
    const loginPage = new LoginPage(page);
    await loginPage.goto();
    await use(loginPage);   // test runs here
    // cleanup code after use() runs after the test
  },
});
```

Then in a spec:

```ts
test('user can log in', async ({ loginPage }) => {
  await loginPage.login('user', 'pass');
});
```

## My notes

- 
