# Creating a Type with a Generic Return Type from a Generic Function

Imagine you have an external library, and you want to extract the return type while also customizing the generic part as per your needs.

```typescript
// External library
function someGenericFunction<P>(data: P) {
  return {
    data,
    functionA: () => {},
    functionB: () => data,
  };
}

// Your code
interface Data {
  a: string;
  b: number;
  c: boolean;
}

type SomeGenericFunctionType = ReturnType<typeof someGenericFunction<Data>>; // TypeScript will throw an error
```

To address this, you can implement the following workaround:

```typescript
class GetDynamicReturnType<T> {
  run(e: T) {
    return someGenericFunction<T>(e);
  }
}

type SomeGenericFunctionType = ReturnType<GetDynamicReturnType<Data>["run"]>;
```

This solution allows you to extract the return type of the generic function while customizing the generic parameter according to your requirements.
