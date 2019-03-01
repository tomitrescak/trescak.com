---
description: >-
  The simple, yet powerful and blazing fast 🚀 component catalogue.
---

# Quick Start

If you do not care about the manual setup and you are ok with Typescript, simply start with [the example from the Luis repo](https://github.com/tomitrescak/luis/tree/master/src/examples/example). This example showcases the simplest setup for Luis, only as a component catalogue.

To start Luis simply run:

```
yarn
yarn run luis
```

Then visit: `http://localhost:9001` and you will see the friendly Luis interface:

![Luis](https://user-images.githubusercontent.com/2682705/53632273-9a082080-3c68-11e9-806a-52ee73e93b75.png)

# Setup

If you wish to configure Luis in your own project, following are the instructions on how we created this project. Please skip steps which you have already performed.

We start with a fresh project, intialise the new node.js project, add Luis, Fuse-Box bundler and initialise the catalogue:

```
mkdir Catalogue
cd Catalogue
yarn init -y
tsc --init
yarn add luis fuse-box
yarn add @types/react
yarn luis --init
```

The last command `yarn luis --init` adds a `src/luis.ts` file to your project. Please see [configuration](#) page for more options on how to init and run luis. When the project is initialised, we are reasdy coding our own component `greeting.ts`:

```ts
import * as React from 'react';
export const Greeting = () => <div>Hello</div>;
```

We import it into the catalogue in the `greeting.story.ts` story file using standard test notation with `describe` and `it`. Each nested `describe` creates a sub-directory in the catalogue.

```ts
import { Greeting } from '../greeting';

describe('Greeting', () => {
  return {
    component: Greeting
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
    // remove whatever your preference is
    require('**.test');
    require('**.story');
    require('**.fixture');
  }
});
```

Once you are ready just run following and go to http://localhost:9001:

```
yarn luis
```

# Tests

This setup does not support tests. If you want to see Luis with tests and snapshots, please see the `snapshots` example (TBA).
