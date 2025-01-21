# Environment Variable Order

Environment variables set using the `export` command are only available for the current session. If you want to make them available for all sessions, you can add them to the `.bashrc` file. And this variables will precede the variables set in the `.env` file.

If you are wondering why the environment variables on the `.env` file are not being used, it is because the environment variables set using the `export` command have precedence over the variables set in the `.env` file. To remove an environment variable, you can use the `unset` command.

```bash
unset VARIABLE_NAME
echo $VARIABLE_NAME
```

### References

[Export command](https://www.man7.org/linux/man-pages/man1/export.1p.html)
[Unset command](https://www.man7.org/linux/man-pages/man1/unset.1p.html)
