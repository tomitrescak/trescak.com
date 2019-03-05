---
description: >-
  Steps to configure Jest
---

## Jest Config

If you want to use Jest as your test runner, you need to use test reporter from Luis to report your test result. This is easily done by adding following to your `jest.config.js`.

```json
{
  "reporters": [
    [
      "luis/jest/reporter",
      {
        "path": "src/summary.ts",
        "merge": true
      }
    ]
  ]
}
```

The reporter has following parameters:

- **path** defines the path to the generated report file, relative to your project root.
- **merge** will merge report with your previous test result. This is particularly useful if you run Jest in watch mode, when new test results will overwrite previous test results. Please note that _merge happens per test suite_; as a result if you use `it.only` you will not obtain result from other tests in the same suite.

## Luis Config

You need to tell Luis where to pick up the test results from, you can do that in your Luis entry file by simply importing the files and passing it to Lous render function. If you start the project from scratch as `luis init --init --tests`, these lines are added for you. Your entry file should look similar to this one:

```ts
import { renderLuis } from 'luis';

// import snapshots and test results
const { snapshots, report } = require('./summary');

renderLuis({
  snapshots, // imported snapshots
  report, // test results
  loadTests: () => {
    // remove whatever your preference is
    require('**.test');
    require('**.story');
    require('**.fixture');
  }
});
```
