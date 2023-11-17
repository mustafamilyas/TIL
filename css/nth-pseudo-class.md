# Pattern on `:nth-` Pseudo Class

In CSS, we can select elements based on their position. There a lot of selectors that we can use, but in here, we will focus on `:nth-` pseudo class selector which are;

- `:nth-child()`
- `:nth-last-child()`
- `:nth-last-of-type()`
- `:nth-of-type()`
  All of them require a pattern as their arguments. Aside from `odd` and `even`, in general the pattern are these.
  > An + B
- A: step size
- n: all of nonnegative integers starting from 0
- B: offset

## Example:

- `:nth-child(5)` select the 5th element
- `:nth-child(2n-1)` select elements number 1, 3 and so on, here is how we got theses:
  - 2 \* 0 - 1 = -1, elements start from 1, so this element is not valid
  - 2 \* 1 - 1 = 1, select element number 1
  - 2 \* 2 - 1 = 3, select element number 3
  - and so on
- `:nth-child(-n + 5)` select elements number 1 to 5

### References

- [:nth-child() - MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/:nth-child)
