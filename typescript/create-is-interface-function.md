# Create is"Interfaces" Function

### Problem

You have a lot of similar objects and you want to do something based on the shape of your objects/interfaces. Your code might look something like this.

```typescript
interface Human {
  name: string;
  age: number;
}

interface Alien {
  name: string;
  color: string;
}

function isHuman(value: any): boolean {
  return (
    typeof value === "object" &&
    value !== null &&
    "name" in value &&
    "age" in value
  );
}

function humanDoSomething(human: Human) {
  // do something
}

const citizens = [
  {
    name: "John",
    age: 20,
  },
  {
    name: "Jane",
    color: "blue",
  },
];

for (const citizen of citizens) {
  if (isHuman(citizen)) {
    humanDoSomething(citizen);
  }
}
```

If you open this in Typescript environment you will see this red squiggly line.
![function type narrowing error](/typescript//assets/function-type-narrowing-error.png)

### Solution

The problem is typescript only knows that the `citizen` pass the `isHuman` function. Typescript doesn't actually know whether the `citizen` is actually human or not. Instead of returning a boolean on `isHuman` function, we can do this.

```typescript
function isHuman(value: any): value is Human {
  return (
    typeof value === "object" &&
    value !== null &&
    "name" in value &&
    "age" in value
  );
}
```

This is called type predicates. We actually return a boolean, but we also tell Typescript, "Hey, this value is compatible with this type".

#### Further Reading

[Using type predicates](https://www.typescriptlang.org/docs/handbook/2/narrowing.html#using-type-predicates)
