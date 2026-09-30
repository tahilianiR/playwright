# Debugging

```bash
npx playwright test --debug          # step through with the Inspector
npx playwright test --ui             # UI mode with time-travel
npx playwright codegen example.com   # record actions into code
```

Pause inside a test:

```ts
await page.pause();
```

## Trace viewer

With `trace: 'on-first-retry'` in the config, failed-then-retried tests save a trace. Open it with:

```bash
npx playwright show-trace test-results/<folder>/trace.zip
```

The trace shows every action, a DOM snapshot, network calls and console logs.

## My notes

- 
