### workers 

default - workers: process.env.CI ? 1 : undefined means 1 worker on CI, and Playwright’s built-in default (half the cores) on your machine.

```ts
fullyParallel: true,
workers: process.env.CI ? 1 : undefined,
```


My local machine has :
cores : 6
logical processors : 12

when I ran default playwright framework I got console message as  - Running 6 tests using 6 workers

BECAUSE : Your CPU has 6 cores and 12 logical processors. Each core runs 2 threads (hyper-threading), and Playwright counts logical processors, not physical cores. Half of 12 is 6 workers, which matches the “using 6 workers” line.


### Notes
You can control the maximum number of parallel worker processes via command line or in the configuration file.
```ts
npx playwright test --workers 4
```


