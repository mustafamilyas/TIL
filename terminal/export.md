# Export command

- This command only applies to Unix-based systems.
- `export` command is used to export environment variables.
- It is used to set environment variables for the current session or to set environment variables for a script.
- It doesn't persist after the session ends and other sessions won't have access to the environment variables.
- Here is the syntax:

```bash
export VARIABLE_NAME=value
```

- And to use the environment variable, you can use the following syntax:

```bash
# To use the environment variable, don't forget to use the dollar sign.
echo $VARIABLE_NAME
```

### References

- [Export comand](https://pubs.opengroup.org/onlinepubs/9699919799/utilities/V3_chap02.html#export)
