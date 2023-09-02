# Difference between interface and type

We can use both of them interchangeably, but there are some different behavior between both of them.

1. Both of them can extend other interfaces & types

```typescript
interface User {
  username: string;
  password: string;
}
interface Admin extends User {
  role: "Admin";
}

// extend via intersection
type User = {
  username: string;
  password: string;
};

type Admin = User & {
  role: "Admin";
};
```

There are a little bit difference when extending multiple interfaces / types with similar attribute. `interface` will throw an error on the extended interface but work just fine when setting a variable on that type, but `type` will set that attribute into `never`.

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
// You will see error below when hovering C
// Interface 'C' cannot simultaneously extend types 'A' and 'B'. Named property 'a' of types 'A' and 'B' are not identical.

const c: C = {
  a: "a",
  b: "b",
};
// but work just fine when seting the variable, just make sure use either shape A or B, can't be the mixture of both of them.
```

2. Both of

3. Typing twice will extend interfaces, but will throw a duplicate error on type
