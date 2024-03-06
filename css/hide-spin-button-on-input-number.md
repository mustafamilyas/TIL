# Hide Spin Button on Input Number Type

Usually, some html element have their own default UI implementation specific to browser. In some cases, you might want to hide the spin button on input number type. You can do this by using the following CSS.

```css
/* on non-webkit based browser (firefox) */
.input[type="number"] {
  -moz-appearance: textfield;
  appearance: textfield;
}

/* on webkit based browser */
.input[type="number"]::-webkit-outer-spin-button,
.input[type="number"]::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
```

## References

- [Can I hide the HTML5 number input’s spin box? | StackOverflow](https://stackoverflow.com/questions/3790935/can-i-hide-the-html5-number-input-s-spin-box)
- [Appearance | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/appearance)
