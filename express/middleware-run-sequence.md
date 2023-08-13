# Middleware Run Sequence

Middleware is processed from left to right. Take a look at this code.

```javascript
const middleware1 = (req, res, next) => {
  console.log("middleware 1");
  next();
};
const middleware2 = (req, res, next) => {
  console.log("middleware 2");
  next();
};
const middleware3 = (req, res, next) => {
  console.log("middleware 3");
  next();
};
const handler = (req, res) => {
  // api handler
};
app.get("/", middleware1, middleware2, middleware3, handler);
```

`middleware1` will run first, `middleware2` will come second, and so on. But you **need** to call `next()` to execute the next middleware / API handler. If **not** then, it will **never** be called. Take a look below.

```javascript
const middleware1 = (req, res, next) => {
  console.log("middleware 1");
};
const middleware2 = (req, res, next) => {
  console.log("middleware 2");
  next();
};
const middleware3 = (req, res, next) => {
  console.log("middleware 3");
  next();
};
const handler = (req, res) => {
  // api handler
};
app.get("/", middleware1, middleware2, middleware3, handler);
```

When we do get a request on the `'/'` route, only `middleware1` runs, as this function is never called `next()` on its function body.

This also apply if we register middlewares by using array instead.

```javascript
app.get("/", [middleware1, middleware2, middleware3], handler);
```
