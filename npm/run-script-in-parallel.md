# Run Script in Parallel

When you want to run multiple commands as npm script, sometimes you use `&` between commands. But this makes the command run synchronously, which is okay if you intend to do that. But to run the command in parallel, you can use `npm-run-all` or `concurrently` package.

## npm-run-all

```json
{
  "scripts": {
    "start": "npm-run-all --parallel start:server start:client",
    "start:server": "ts-node-dev --respawn --transpile-only src/server.ts",
    "start:client": "next dev"
  }
}
```

or if you want to make it even shorter, you can use the alias

```json
  "scripts": {
    "start": "run-p start:server start:client",
    "start:server": "ts-node-dev --respawn --transpile-only src/server.ts",
    "start:client": "next dev"
  }
}
```

## concurrently

```json
{
  "scripts": {
    "start": "concurrently \"npm run start:server\" \"npm run start:client\"",
    "start:server": "ts-node-dev --respawn --transpile-only src/server.ts",
    "start:client": "next dev"
  }
}
```

## Reference

- [npm-run-all](https://www.npmjs.com/package/npm-run-all)
- [concurrently](https://www.npmjs.com/package/concurrently)
