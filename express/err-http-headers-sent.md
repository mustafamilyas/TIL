# Error ERR_HTTP_HEADERS_SENT

### Problem

```
Error [ERR_HTTP_HEADERS_SENT]: Cannot set headers after they are sent to the client
```

### Cause

This is a soft error I think. It doesn't make our server crash. This is caused when you set the header / send a response **after** a response has already been sent. Which makes sense, one request - one response.
Take a look at the code below.

```javascript
app.get("/", (req, res) => {
  res.json({ message: "Hello world!" });
  // it is still running
  console.log("this is a test");
  // but it will throw an error if we try to send another response
  res.json({ message: "Hello world! test" });
});
```

### Solution

If you have a conditional response, it is encouraged to return immediately after the request has been sent. Take a look at the code below.

```javascript
app.get("/", (req, res) => {
  const authorization = req.headers.authorization;
  if (!authorization) {
    res.status(401);
    res.json({ message: "not authorized" });
    // don't forget to return
    return;
  }

  res.json({ message: "welcome" });
});
```
