# Extending Multiple Interfaces or Types with Similar Attributes

There is a difference when extending multiple interfaces/types with similar attributes. `interface` will throw an error on the extended interface but work just fine when setting a variable on that type, but `type` will set that attribute into `never`.

Interface behavior below

```typescript
interface A {
  a: string;
  b: string;
}

interface B {
  a: number;
  b: number;
}

interface C extends A, B {}
// You will see the error below when hovering over C interface
// Interface 'C' cannot simultaneously extend types 'A' and 'B'. Named property 'a' of types 'A' and 'B' are not identical.

const c1: C = {
  a: "a",
  b: "b",
};
const c2: C = {
  a: 1,
  b: 2,
};
// but works just fine when setting the variable, just make sure to use either shape A or B, can't be a mixture of both of them.

const c: C = {
  a: "a",
  b: 2,
};
// above code will error
```

Type behavior below

```typescript
type A = {
  a: string;
  b: string;
};

type B = {
  a: number;
  b: number;
};

type C = A & B;
// ^ works just fine

const c: C = {
  a: "a",
  b: "b",
};
//When you hover "a" or "b", you will see this error
// Type 'string' is not assignable to type 'never'
```
