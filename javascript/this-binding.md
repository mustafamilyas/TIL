# This Binding

`this` is a special keyword in JavaScript that refers to the object that is currently executing the function. It is a reference to the object that owns the function. It is a reference to the object that is currently executing the function.

## Implicit Binding

```javascript
const person = {
  name: "John",
  sayName: function () {
    console.log(this.name);
  },
};

person.sayName(); // John
```

In the above example, `this` refers to the `person` object. This is called **implicit binding**. It means that `this` is bound to the object that is currently executing the function. Here is similar example that produces similar result

```javascript
function sayName() {
  console.log(this.name);
}

const person = {
  name: "John",
  sayName: sayName,
};

person.sayName(); // John
```

In the above example, `this` is bound to the `person` object because `person` is the object that is currently executing the function.

## Explicit Binding

You can also explicitly bind `this` to an object using `call`, `apply`, or `bind` method.

```javascript
function sayName() {
  console.log(this.name);
}

const person = {
  name: "John",
};

sayName.call(person); // John
sayName.apply(person); // John
sayName.bind(person)(); // John
```

In the above example, `this` is explicitly bound to the `person` object using `call`, `apply`, and `bind` method.

## New Binding

When you use `new` keyword to create an instance of a function, `this` is bound to the new object.

```javascript
function Person(name) {
  this.name = name;
}

const john = new Person("John");
console.log(john.name); // John
```

In the above example, `this` is bound to the `john` object because new keyword is used to create an instance of the `Person` function. This is called **new binding**.

## Arrow Function

Arrow function does not have its own `this`. It uses the `this` from the surrounding code. This is called **lexical binding**.

```javascript
const person = {
  name: "John",
  sayName: () => {
    console.log(this.name);
  },
};

person.sayName(); // undefined
```

In the above example, `this` is not bound to the `person` object. It is bound to the global object. This is because arrow function does not have its own `this`. It uses the `this` from the surrounding code. In this case, the surrounding code is the global object.
