# Installation and setup

Start a new Playwright project with TypeScript:

```bash
npm init playwright@latest
```

This creates:

- `playwright.config.ts` – global settings (browsers, timeouts, reporters)
- `tests/` – where spec files live
- `tests-examples/` – a sample test to read through

Install or update the browsers later with:

```bash
npx playwright install
```

## Run tests

```bash
npx playwright test                 # all tests, headless
npx playwright test login.spec.ts   # one file
npx playwright test --headed        # watch the browser
npx playwright test --ui            # UI mode, great for learning
npx playwright show-report          # open the last HTML report
```

## My notes

- 
