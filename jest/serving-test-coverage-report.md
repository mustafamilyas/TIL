# Serving Coverage Static Files

To serve report files, you can use the `serve` command from the `http-server` package.

```bash
npx http-server coverage/lcov-report -p 8080
```

This will serve the coverage report on `http://localhost:8080`. Actually we have another alternative to serve the coverage report using the `npx` command.

```bash
npx serve coverage/lcov-report
```

But this library will not properly serve the coverage report, as jest coverage report contains an html with this format `/path/to/file.ts.html`. Serve does not recognize this format out of the box and will return a 404 error. So, it is recommended to use the `http-server` package to serve the coverage report.
