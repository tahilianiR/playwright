# Locators

Locators find elements on the page. They wait automatically and re-query the DOM each time they're used, so they don't go stale.

## Preferred order

1. `getByRole` – how users and screen readers see the page
2. `getByLabel` – form fields
3. `getByPlaceholder`, `getByText`
4. `getByTestId` – when the app has `data-testid` attributes
5. `locator('css or xpath')` – last resort

```ts
await page.getByRole('button', { name: 'Sign in' }).click();
await page.getByLabel('Email').fill('ramesh@example.com');
await page.getByTestId('kol-grid').isVisible();
```

## Narrowing down

```ts
const row = page.getByRole('row').filter({ hasText: 'Oncology' });
await row.getByRole('button', { name: 'Edit' }).click();

page.getByRole('listitem').nth(2);
page.getByRole('listitem').first();
```

## My notes

- 
