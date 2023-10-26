# Get Argument Types of Constructor

```typescript
class Foo {
  constructor(a: string, b: number) {}
}

type FooConstructorArgs = ConstructorParameters<typeof Foo>; // [string, number]
```

if you want to create a generic function and want to get the argument types of the constructor, you can do this.

```typescript
//This will throw an error
function wrongCreateInstance<T>(
  constructor: T,
  ...args: ConstructorParameters<T>
): InstanceType<T> {
  return new constructor(...args);
}

//This will work
function createInstance<T extends new (...args: any[]) => any>(
  constructor: T,
  ...args: ConstructorParameters<T>
): InstanceType<T> {
  return new constructor(...args);
}

const foo = createInstance(Foo, "a", 1); // foo is Foo
```

The hack is on `T extends new (...args: any[]`
