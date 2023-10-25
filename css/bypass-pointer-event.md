# Bypass Pointer Event of an Element

If you have layout that has an element that stacked on top of another element, and you want to make the element below can be clicked, you can use `pointer-events: none` on the element that stacked on top of the element that you want to click.

```css
.element-on-top {
  pointer-events: none;
}
```

## References

- [pointer-events - MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/pointer-events)
