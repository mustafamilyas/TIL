# Posible Cause Tailwind Don't Generate Selected Class on a Component

### Problem

You already installed Tailwind, but some class on some components is not generated although you see that you already applied the class properly.

### Causes

Most likely you haven't set the path to your component path on the tailwind config. To solve this just include your components into `content` property on the tailwind config

```typescript
// tailwind.config.ts
/** @type {import('tailwindcss').Config} */
export default {
  content: [
    // insert here
    "./path/to/your/component/**/*.{ts,tsx}",
  ],
};
```
