# Fix Issue Module not found: Can't resolve '@swc/helpers/\_/\_interop_require_default'

When you run next build, you may see this error:

```
Module not found: Can't resolve '@swc/helpers/_/_interop_require_default'

Import trace for requested module:
./node_modules/next/dist/client/components/navigation.js
./node_modules/next/navigation.js
./components/layout/components/header/header.tsx
./components/layout/layout.tsx
./pages/_app.page.tsx
```

Here is the linked [issue thread](https://github.com/vercel/next.js/issues/48593). To fix this, you need to replace `swc/helpers` on your `package.lock`. I use `yarn`, so I can do this in my `package.json`.

```json
{
  "resolutions": {
    "next/@swc/helpers": "0.4.36"
  }
}
```
