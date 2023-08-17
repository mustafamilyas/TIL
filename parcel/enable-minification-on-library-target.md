# Enabling Minification for Library Targets

By default, Parcel enables [minification](https://parceljs.org/features/targets/#optimize:~:text=optimize-,%23,-Enables%20or%20disables). However, if you include `main`, `module`, `browser`, and `types` fields in your `package.json` file, Parcel assumes that you are constructing a library and will deactivate the minification.

```json
// package.json
{
  "name": "my-library",
  "version": "1.0.0",
  "source": "src/index.js",
  "main": "dist/main.js",
  "module": "dist/module.js",
  "types": "dist/types.d.ts"
}
```

To enable minification, you can introduce an `optimize` field in the `package.json` file.

```json
// package.json
{
  "name": "my-library",
  "version": "1.0.0",
  "source": "src/index.js",
  "main": "dist/main.js",
  "module": "dist/module.js",
  "types": "dist/types.d.ts",
  "targets": {
    "main": {
      "optimize": true
    }
  }
}
```

### Further Reading

- [Library Targets](https://parceljs.org/features/targets/#library-targets:~:text=%7D%0A%20%20%7D%0A%7D-,Library%20targets,-%23)
