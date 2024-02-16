# Error [ERR_REQUIRE_ESM]: require() of ES Module

I have found this error when I tried to run a jest test file. The error message is:

```bash
Error [ERR_REQUIRE_ESM]: require() of ES Module ...
```

Current working solution is to remove `package-lock.json` and run `npm install` again. But this is not sustainable solution. I need to find a better solution for this.
