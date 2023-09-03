# Extending Multiple Interfaces or Types with Similar Attributes

There is a difference when extending multiple interfaces/types with similar attributes. `interface` will throw an error on the extended interface but work fine when setting a variable on that type, but `type` will set that attribute into `never`.

Interface behavior below

```typescript
interface A {
  a: string;
  b: string;
  e: string;
}

interface B {
  a: number;
  b: number;
  f: string[];
}

interface C extends A, B {}
// You will see the error below when hovering over C interface
// Interface 'C' cannot simultaneously extend types 'A' and 'B'. Named property 'a' of types 'A' and 'B' are not identical.

const c1: C = {
  a: "a",
  b: "b",
  e: "e",
  f: ["f"],
};
// but works just fine when setting the variable, but 'a' will be the first type from extending which is 'string'

const c2: C = {
  a: 1,
  b: 2,
  e: "e",
  f: ["f"],
};

const c: C = {
  a: "a",
  b: 2,
  e: "e",
  f: ["f"],
};
// above code will error

// --------------------
interface C extends A, B {
  a: boolean;
}
// When you hover C, it still showing an error, but now, the resolved type of "a" is a boolean
// --------------------
interface A {
  a: unknown; // or any
}

interface B {
  a: unknown; // or any
}

interface C extends A, B {
  a: boolean;
}
//This will not throw an error
//But this is not a proper fix IMO
```

Type behavior below

```typescript
type A = {
  a: string;
  b: string;
  e: string;
};

type B = {
  a: number;
  b: number;
  f: string[];
};

type C = A & B;
// ^ works just fine

const c: C = {
  a: "a",
  b: "b",
  e: "e",
  f: ["f"],
};
//When you hover "a" or "b", you will see this error
// Type 'string' is not assignable to type 'never'
```

### Solution

In my honest opinion, if we extend interface(s) with a similar property, it just means we need to rearrange the typing, for example, instead of this.

```typescript
interface HumanWithLeg {
  skills: unknown;
  leg: number;
}

interface HumanWithHand {
  skills: unknown;
  hand: number;
}

interface Human extends HumanWithLeg, HumanWithHand {
  skills: string[];
  age: number;
}
```

We can extract the type into this

```typescript
interface CreatureWithLeg {
  leg: number;
}

interface CreatureWithHand {
  hand: number;
}

interface HumanWithLeg extends CreatureWithLeg {
  skills: string[];
}

interface HumanWithHand extends CreatureWithHand {
  skills: string;
}

interface Human extends CreatureWithHand, CreatureWithLeg {
  skills: string[];
  age: number;
}
```
