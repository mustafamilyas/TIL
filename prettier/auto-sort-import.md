# Setup Auto Sort Import Statement on JS App

The library used is [Prettier plugin sort imports](https://github.com/trivago/prettier-plugin-sort-imports).

1. Install the dependencies

```bash
npm install --save-dev @trivago/prettier-plugin-sort-imports
# or
yarn add --dev @trivago/prettier-plugin-sort-imports
```

2. Add the config into the prettier config file

```javascript
module.exports = {
  printWidth: 80,
  tabWidth: 4,
  trailingComma: "all",
  singleQuote: true,
  semi: true,

  // add below configs

  plugins: ["@trivago/prettier-plugin-sort-imports"]

  // group and sort import using regex, third-party library will be shown on the top unless specified
  importOrder: ["^@core/(.*)$", "^@server/(.*)$", "^@ui/(.*)$", "^[./]"],

  //If you want to control how the third-party library will be shown, you can do this instead

  importOrder: [
    "^@core/(.*)$",
    "<THIRD_PARTY_MODULES>", // this is for the third party libray
    "^@server/(.*)$",
    "^@ui/(.*)$",
    "^[./]",
  ],

  //Add line space after each grouped import
  importOrderSeparation: true,
  importOrderSortSpecifiers: true,
};
```
