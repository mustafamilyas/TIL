# Infer Keyword

`infer` is a keyword in typescript that can deduce a type, store them like a variable, and we can use that later.

```typescript
type ToPrimitiveValue<T> = T extends (...args: any[]) => infer R
  ? R
  : T extends { value: infer V }
  ? V
  : T extends Array<infer A>
  ? A
  : T extends object
  ? string
  : T;

type Test1 = ToPrimitiveValue<() => number>; // number
type Test2 = ToPrimitiveValue<string>; // string
type Test3 = ToPrimitiveValue<{ value: string }>; // string
type Test4 = ToPrimitiveValue<boolean[]>; // boolean
type Test5 = ToPrimitiveValue<{ a: boolean; c: number[] }>; // string
type Test6 = ToPrimitiveValue<() => string | number>; // string | number
```

`infer` **can only be within** `extends` clause of conditional type.
