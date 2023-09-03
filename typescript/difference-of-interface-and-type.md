# Difference between `interface` and `type`

We can use both of them interchangeably, but there are some different behaviors between both of them.

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

There are a few differences when extending multiple interfaces/types with similar properties, which you can read [here](/typescript/extending-multiple-interface-or-type-with-similar-attribute.md).

2. Declaration merging. When there are multiple declarations, `interface` will merge the property but `type` will throw an error.

```typescript
interface Animal {
  species: string;
}

interface Animal {
  height: number;
  weight: number;
}

// Animal interface merged
const animal: Animal = {
  species: "dog",
  height: 12,
  weight: 23,
};

// ------------------
type Animal = {
  species: string;
};

type Animal = {
  height: number;
  weight: number;
};
//When you hover Animal type, you will below error
// Duplicate identifier 'Animal'.ts(2300)

const animal: Animal = {
  species: "dog",
  height: 12,
  weight: 23,
};
```

3. `type` can define primitive types but `interface` can only define the shape of an object.

```typescript
type Value = string | number;
type Operator = "+" | "-" | "*" | "/";

interface Calculator {
  calculate: (a: Value, b: Value, operator: Operator) => number;
}
```
