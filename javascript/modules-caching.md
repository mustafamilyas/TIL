# Modules Caching

When you import a module, it will only run once. Node JS or browser will cache the module and return the same instance when you import it again. This is useful when you want to create a singleton module or you want to attach an event handler that load a module dynamically.

```javascript
// foo.js
console.log("foo");

export const foo = "foo";
```

```javascript
// index.js
import "./foo.js";
import "./foo.js";
import "./foo.js";
```

When you run `node index.js`, you will only see `foo` once.

```bash
$ node index.js
foo
```

This also apply to common js module.

### Reference

- [Modules in Javascript](https://exploringjs.com/es6/ch_modules.html#sec_modules-in-javascript)
- [Modules Caching](https://nodejs.org/docs/latest/api/modules.html#modules:~:text=THROW%20%22not%20found%22-,Caching,-%23)
