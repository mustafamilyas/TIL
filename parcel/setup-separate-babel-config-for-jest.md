# Configuring Separate Babel Configuration for Jest Environment

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

This is because Parcel already [integrates similar presets](https://parceljs.org/languages/javascript/#babel:~:text=Default-,presets,-%23), and adding the code above could potentially impact performance. However, it's necessary to retain this preset for Jest to function properly, making its removal impossible.

One potential solution involves renaming the `babel.config.js` file to `babel.test.config.js`. Following this, the configuration can be included in the `jest.config.js` file, as shown below:

```javascript
module.exports = {
  transform: {
    "\\.js$": ["babel-jest", { configFile: "./babel.test.config.js" }],
  },
};
```
