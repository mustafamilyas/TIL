# Get Component Props Type

use `React.ComponentProps`

```typescript
type CustomComponentProps = React.ComponentProps<typeof View>;

type HTMLInputProps = React.ComponentProps<"input">;
```

If you know the nature of the component, whether the component accepts `ref` or not, please use `ComponentPropsWithRef` or `ComponentPropsWithoutRef` instead.

```typescript
type CustomComponentProps = React.ComponentPropsWithoutRef<typeof View>;

type HTMLInputProps = React.ComponentPropsWithRef<"input">;
```
