# Overriding The Default Selection Behavior Using CSS

We can do that by using `::selection` selector, as you can see below

```css
/* global selector */
::selection {
  background: #ffb7b7; /* WebKit/Blink Browsers */
}
::-moz-selection {
  background: #ffb7b7; /* Gecko Browsers */
}

/* specific selector */
.some-class::selection {
  color: #ffb7b7; /* WebKit/Blink Browsers */
}
.some-class::-moz-selection {
  color: #ffb7b7; /* Gecko Browsers */
}
```

We can safely remove `::-moz-selection` as it is already supported in [firefox](https://caniuse.com/css-selection).

However, this method should be treated with care, as it will impact the accessibility. Make sure the contrast between the background and color should be enough for the reader to be able to read.

## Allowable properties

CSS properties that can be used with `::selection`:

- `color`
- `background-color`
- `text-decoration` and its associated properties
- `text-shadow`
- `-webkit-text-stroke-color`
- `-webkit-text-fill-color`
- `-webkit-text-stroke-width`

### Further Reading

- [::selection - caniuse](https://caniuse.com/css-selection)
- [::selection - mdn](https://developer.mozilla.org/en-US/docs/Web/CSS/::selection)
- [Overriding The Default Text Selection Color With CSS](https://css-tricks.com/overriding-the-default-text-selection-color-with-css/)
