# Set Insertion Order

`Set` is a data structure that enables you to store unique values of any type. One of the special things about `Set` implementation is that it is deterministic in terms of insertion order (it doesn't matter if the item is inserted multiple times). Take a look at the code below.

```typescript
const numberSet = new Set<number>();
numberSet.add(3);
numberSet.add(2);
numberSet.add(100);
numberSet.add(3);

const iterator = numberSet.values();

console.log(iterator.next().value);
// Expected output: 3

console.log(iterator.next().value);
// Expected output: 2

console.log(iterator.next().value);
// Expected output: 100

console.log(Array.from(numberSet));
// Expected output: [3,2,100]
```

This behavior also applies to `Map`, it allows you to be able deterministically do something based on the insertion order like an array but with the superpower of speedy lookups and keeping the values unique.

### Further Reading

- [Set - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set)
- [Why does JS keep insertion order in Set? - Stackoverflow](https://stackoverflow.com/questions/55460303/why-does-js-keep-insertion-order-in-set)
