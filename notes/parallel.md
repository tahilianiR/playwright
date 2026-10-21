## parallelism 

### parallel


fullyParallel is nothing but sequential or parallel 

&emsp;&emsp; fullyParallel - false (by default) - tests runs sequentially  
&emsp;&emsp;&emsp;&emsp;override -> test.describe.configure({ mode: 'parallel' });

&emsp;&emsp;fullyParallel - true - tests run in parallel  
&emsp;&emsp;&emsp;&emsp;override -> test.describe.configure({ mode: 'default' });


```ts
export default defineConfig({
  workers: 4,          // number of parallel workers
  fullyParallel: true, // run all ****tests**** in parallel whereever possible
});
```

If fullyParallel: false (default), files may run in parallel, but tests within the same file typically run sequentially.

Specific File - to run tests in parallel : - 
```ts
test.describe.configure({ mode: 'parallel' });
```


Opt out of fully parallel mode at file level : - 
If your configuration applies parallel mode to all tests using testConfig.fullyParallel, you might still want to run some tests with default settings. You can override the mode per describe:
```ts
test.describe('runs in parallel with other describes', () => {
  test.describe.configure({ mode: 'default' });
  test('in order 1', async ({ page }) => {});
  test('in order 2', async ({ page }) => {});
});
```



### Serial mode (to make tham inter-dependent)
You can annotate inter-dependent tests as serial. If one of the serial tests fails, all subsequent tests are skipped. All tests in a group are retried together.
Using serial is not recommended. It is usually better to make your tests isolated, so they can be run independently.

```ts
test.describe.configure({ mode: 'serial' });
```

### Notes

You can also enable it for a single project only:

```ts
projects: [
  { name: 'chromium', use: { browserName: 'chromium' }, fullyParallel: true },
],
```
can also pass from cli - npx playwright test --fully-parallel

earlier it was like test.describe.parallel() / test.describe.serial() -- still in use but may be phased out in future