# SVG Paint Order

![SVG Paint Order](/css/assets/svg-paint-order.png)

The image shows, svg default behavior (the left side), with transparent stroke (the middle side), and svg with `paint-order` set to `stroke`. There are several things to note:

1. As you can see from the image above, the stroke doesn't start on the outer side of the shape. Instead, they grow both outside and inside.
2. `paint-order` by default set to fill. It means it will draw `fill` first and then `stroke`. This is okay if you don't put the opacity for both `fill` and `stroke`. If you set opacity on one of them, things might become weird as you can see above.

If you want to see the code above, you can click here.

### Further Reading

- [Paint Order - MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/paint-order)
