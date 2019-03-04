---
description: >-
  Luis can visualise your test results
---

Luis is a powerful tool for visualising your test result in a comfortable and visual way. This can be configured for all major test suites.

Test results are visualised directly in the test tree along with following information:

1. Test name
2. Test result
3. Test result info with equality comparation
4. Test length

![Test Viewer](https://user-images.githubusercontent.com/2682705/53708428-8b4b8480-3e87-11e9-8ccf-c2b93c36670d.png)

# Quick Start

If you do not care about the manual setup and you are ok with Typescript, simply start with [the example from the Luis repo](https://github.com/tomitrescak/luis/tree/master/src/examples/with-tests). This example showcases setup for Luis with tests and snapshots.

To start Luis simply run:

```
yarn
yarn test
yarn run luis
```

Then visit: `http://localhost:9001` and you will see the friendly Luis interface:

![Luis](https://user-images.githubusercontent.com/2682705/53632273-9a082080-3c68-11e9-806a-52ee73e93b75.png)

# Manual Setup

If you wish to configure Luis in your own project, following are the instructions on how we created this project. Please skip steps which you have already performed. Also, this setup uses Jest as your test runner. Please read the documentation related to your test runner.

We start with a fresh project, intialise the new node.js project, add Luis, Fuse-Box bundler and initialise the catalogue:

```
mkdir Catalogue
cd Catalogue
yarn init -y
tsc --init
yarn add luis fuse-box jest-cli react-test-renderer ts-jest typescript @types/react @types/jest
yarn ts-jest config:init
yarn luis --init --tests
```

The last command `yarn luis --init --tests` adds a `src/luis.ts` file to your project. Please see [cli](cli) page for more options on how to init and run luis.

We need to configure our test runner to report data needed by luis. In your `jest.config.js` file add a following line:

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

The reporter contains some configuration options for setting the target files or merging results. Please explore these in the documentation. We are now ready to code and test our component `greeting.ts`:

```ts
import * as React from 'react';

type Props = { name: string };
export const Greeting: React.FC<Props> = ({ name }) => <div>Hello {name}</div>;
```

We import it into the catalogue in the `greeting.test.ts` spec file using standard test notation with `describe` and `it`. Each nested `describe` creates a sub-directory in the catalogue.

```ts
import React from 'react';
import { create } from 'react-test-renderer';

import { Greeting } from '../greeting';

describe('Greeting', () => {
  const Component = () => <Greeting name="Tomas" />;

  it('renders correctly', () => {
    expect(create(<Component />)).toMatchSnapshot();
  });

  it('fails', () => {
    expect('123').toEqual('456');
  });

  return {
    component: Component
  };
});
```

In our example, all components are added to catalogue in `*.test` files. You can also add components in following files:

- `*.test`
- `*.fixture`
- `*.story`

or in following directories:

- `/__tests__/*`
- `/__fixtures__/*`
- `/__stories__/*`

The main file, where we load all tests is in the default location `src/luis.ts`, with the content below.

```ts
import { renderLuis } from 'luis';

renderLuis({
  loadTests: () => {
    require('**.test');
  }
});
```

Once you are ready just run following and go to http://localhost:9001:

```
yarn luis
```

To see the snapshots
