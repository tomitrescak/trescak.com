---
description: >-
  LUIS: List of UIs ;) Component development, test viewer, snapshot management
---

# Wicked Luis

![](https://user-images.githubusercontent.com/2682705/31411885-c22597e4-ae5e-11e7-8ea0-fa93b62596fd.png)

Luis aims to simplify React component development and testing along with [component maintenance, and presentation](./luis/catalogue.md). It [visualises test results](./luis/test.md) and [compares your stored code-based or image-based snapshots](./luis/snapshots.md). It can run as a standalone application, or [ run as a part of your app](./luis/route.md). It supports several bundlers such as [Fuse-Box](./luis/fuse-box.md), [Parcel](./luis/parcel.md) or [Webpack](./luis/webpack.md) and several testing frameworkd, such as [Jest](./luis/jest.md), [Mocha](./luis/mocha.md) or [Jasmine](./luis/jasmine.md). It even has a [cli](./luis/cli) to get you started and a [cool **dark theme**](./luis/options.md) :)

### Alternatives

Before we go about trying to convince you how awesome Luis are, please consider also alternatives, which server us as a great source of inspiration:

1. [StoryBook](https://github.com/storybooks/storybook) - The first one, the most famous one, the most flexible one
2. [Cosmos](https://github.com/react-cosmos/react-cosmos) - The coolest one, we took [proxies](proxies.md) from these guys
3. [Styleguidist](https://github.com/styleguidist/react-styleguidist) - The long one

### Easy as 1, 2 ... 3.

It is very easy and blazing fast to start with Luis. If you are ok with yarn, Typescript and Fuse-Box as your bundler:

```
$ yarn add luis fuse-box --dev
$ yarn luis init
$ yarn luis
```

Go to `http://localhost:9001` and behold ;). Go to `src/luis.ts` to add your configuration or tests.

![LUIS Interface](https://user-images.githubusercontent.com/2682705/31411377-29cb8298-ae5d-11e7-9817-6b1368af5954.gif)

### Test Engines

LUIS works out of the box with Jest just add {reporter: "luis/reporter"} to your jest.config.js and watch magic unravel. Mocha and Jasmine are easy to plug in. Check out the docs to get there!

![Test Suites](https://user-images.githubusercontent.com/2682705/53707895-08c1c580-3e85-11e9-8795-9653f7042191.png)

### Bundlers

We developed Luis on FuseBox because we love speed and stability, and we ❤️ Typescript! Yet, we understand your love for other bundlers. Check out the docs how to make Luis work with Parcel and Webpack!

![Bundlers](https://user-images.githubusercontent.com/2682705/53707898-0c554c80-3e85-11e9-800e-67d9fa33a584.png)

## Contributors

- Tomas Trescak (tomitrescak)
- ... You ?
