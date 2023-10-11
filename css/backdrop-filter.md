# Backdrop Filter

You can use the' backdrop-filter' property if you want to apply graphical effects like blur or color shifting to the area behind an element.

```css
.backdrop-filter {
  backdrop-filter: blur(10px);
}
```

Usually, you need to set the `background-color` to `transparent` to see the effect or any opacity value less than `1`. You need to set it using `background` property, not through `opacity` property

```css
/* works */
.backdrop-filter {
  backdrop-filter: blur(10px);
  background-color: transparent;
}
/* doesn't works */
.backdrop-filter {
  background: black;
  backdrop-filter: blur(10px);
  opacity: 0.5;
}
```

You can see the pen [here](https://codepen.io/redmaze/pen/dywrXYZ).

### Further Reading

- [Backdrop Filter - MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/backdrop-filter)
