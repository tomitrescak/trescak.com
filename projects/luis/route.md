---
description: >-
  If you wish to render Luis as part of your app, Luis is here to help. Make sure you code-split it from your app.
---

# Quick Start

If you do not care about the manual setup and you are ok with Typescript, Jest and FuseBox, simply start with [this example from the Luis repo](https://github.com/tomitrescak/luis/tree/master/src/examples/custom-route). This example showcases setup for Luis as part of your app routed with react router.

To start your app simply run:

```
yarn start
```

- Visit: `http://localhost:3000` and you will see your app.
- Visit: `http://localhost:3000/luis` and you will see your friendly Luis interface.

# Manual Setup

To include Luis in your app you need to perform following steps:

1. Update your `fuse.js` file to automatically import all tests
2. Import semantic-ui styles.
3. Lazily load Luis in your route.

##
