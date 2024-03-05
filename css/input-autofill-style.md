# Input Autofill Style

Browser's default style for input autocomplete is not always the best fit for the design. You can style overrided the default style using the `:-webkit-autofill` pseudo-element.

```css
input:-webkit-autofill,
input:-webkit-autofill:hover,
input:-webkit-autofill:focus,
input:-webkit-autofill:active {
  -webkit-background-clip: text;
  -webkit-text-fill-color: #ffffff;
  transition: background-color 5000s ease-in-out 0s;
  box-shadow: inset 0 0 20px 20px #23232329;
}
```

### References

- [Removing input background colour for Chrome autocomplete?](https://stackoverflow.com/questions/2781549/removing-input-background-colour-for-chrome-autocomplete)
