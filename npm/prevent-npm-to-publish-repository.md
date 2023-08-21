# Prevent Accidentally Publishing Repository

The easiest way to do that is to add `private: true` on the `package.json`.

```json
// package.json
{
  "name": "my-library",
  "version": "1.0.0",
  "private": true,
  "source": "src/index.js",
  "main": "dist/main.js",
  "module": "dist/module.js",
  "types": "dist/types.d.ts"
}
```

So when you run `npm publish`, it will throw an error as you can see below.

```
npm ERR! code EPRIVATE
npm ERR! This package has been marked as private
npm ERR! Remove the 'private' field from the package.json to publish it.
```
