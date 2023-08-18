# Configuring Separate Babel Configuration for Jest Environment

In the past, the [Parcel compiler relied on Babel](https://parceljs.org/blog/beta3/#10x-faster-javascript-compiler-written-in-rust-%F0%9F%9A%80) for its operation. However, due to Babel being relatively slow in today's standards, as it's implemented in JavaScript, Parcel version 2 took a different approach. The compiler was redeveloped in Rust, utilizing [SWC](https://swc.rs/), resulting in significantly improved speed.

When it comes to configuring [Jest](https://jestjs.io/docs/getting-started#using-babel), it's customary to set up the Babel configuration in the `babel.config.js` file. However, doing so might trigger a warning like the one below:

```javascript
// babel.config.js
module.exports = {
  presets: [["@babel/preset-env", { targets: { node: "current" } }]],
};
```

```
@parcel/transformer-babel: Parcel includes transpilation by default. Babel config babel.config.js contains only redundant presets. Deleting it may
significantly improve build performance.

  /Users/ilyasayunda/Documents/code/merge-classnames/babel.config.js:1:1
  > 1 | module.exports = {
  >   | ^
    2 |   presets: [["@babel/preset-env", { targets: { node: "current" } }]],
    3 | };

  💡 Delete babel.config.js
  📝 Learn more: https://parceljs.org/languages/javascript/#default-presets
```

This is because Parcel already integrates similar presets, and adding the code above could potentially impact performance. However, it's necessary to retain this preset for Jest to function properly, making its removal impossible.

One potential solution involves renaming the `babel.config.js` file to `babel.test.config.js`. Following this, the configuration can be included in the `jest.config.js` file, as shown below:

```javascript
module.exports = {
  transform: {
    "\\.js$": ["babel-jest", { configFile: "./babel.test.config.js" }],
  },
};
```
