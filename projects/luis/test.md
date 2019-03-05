---
description: >-
  Luis can visualise your test results
---

Luis can visualise your test result alongside your components. This can be configured for all major test suites ([Jest](jest.md), [Mocha](mocha.md), [Jasmine](jasmine.md)). Test results display following information:

1. Test name
2. Test result
3. Test length
4. Test snapshots
5. Total number of passing and failing tests of all test suites, as well as per test suite

![Test Viewer](https://user-images.githubusercontent.com/2682705/53708428-8b4b8480-3e87-11e9-8ccf-c2b93c36670d.png)

# Quick Start

If you do not care about the manual setup and you are ok with Typescript, Jest and FuseBox, simply start with [this example from the Luis repo](https://github.com/tomitrescak/luis/tree/master/src/examples/with-tests). This example showcases setup for Luis with tests and snapshots.

To start this example simply run:

```
yarn
yarn test
yarn run luis
```

Important here is to run tests with `yarn test`. This generates your test results. Visit: `http://localhost:9001` and you will see the friendly Luis interface:

![Luis](https://user-images.githubusercontent.com/2682705/53632273-9a082080-3c68-11e9-806a-52ee73e93b75.png)

# Manual Setup

> If you are only adding tests to your existing Luis catalogue, please skip to the [Configure Test Runner][testrunner].

If you wish to configure Luis in your own project for your own combination of tools, following are the instructions on how we created this project. Please skip steps which you have already performed and use your own tool-chain. Also, this setup uses Jest as your test runner and FuseBox as your bundler. If you want to use something different, please read the documentation related to your tool-chain.

## Create Project

We start with a fresh project, intialise the new node.js project, add Luis, Fuse-Box bundler and initialise the catalogue:

```
mkdir Catalogue
cd Catalogue
yarn init -y
tsc --init
yarn add luis fuse-box jest-cli react-test-renderer
yarn add ts-jest typescript @types/react @types/jest @types/react-test-renderer @types/node
yarn ts-jest config:init
yarn luis --init --tests jest
```

Please visit the `tsconfig.json` to adjust your values. We have enabled `jsx: react` to enable React.

The last command `yarn luis --init --tests jest` adds a `src/luis.ts` file to your project. Please see [cli](cli) page for more options on how to init and run luis. Also, we are using Jest in this example. Please see the documentation for your test framework ([Jest](jest.md), [Mocha](mocha.md), [Jasmine](jasmine.md)).

## Create Component and Test

The reporter contains some configuration options for setting the target files or merging results. Please explore these in the documentation. We are now ready to code and test our component `greeting.tsx`:

```ts
import * as React from 'react';

type Props = { name: string };
export const Greeting: React.FC<Props> = ({ name }) => <div>Hello {name}</div>;
```

We import it into the catalogue in the `greeting.test.tsx` spec file using standard test notation with `describe` and `it`. Each nested `describe` creates a sub-directory in the catalogue.

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

## Run Tests and Luis

We need to run tests, you can either run tests once with `yarn jest` or run them in watch mode, e.g. `yarn jest --watch`. It is advisable to run all tests at least once.

```
yarn jest
```

Once you are ready just run following and go to http://localhost:9001:

```
yarn luis
```

### Custom Setup

> In our example, all components are added to catalogue in `*.test` files. You can also add components in following files:
>
> - `*.test`
> - `*.fixture`
> - `*.story`
>
> or in following directories:
>
> - `/__tests__/*`
> - `/__fixtures__/*`
> - `/__stories__/*`

### Snapshots

You can also visualise the snapshot and compare it for possible errors:

![Snapshots](https://user-images.githubusercontent.com/2682705/53784422-4e57be80-3f69-11e9-9d42-85ff87c5271e.gif)

To learn more about snapshots please see [snapshots](snapshots.md) section.
