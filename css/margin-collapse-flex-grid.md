# Margin Collapse on Flex & Grid Elements

<iframe height="300" style="width: 100%;" scrolling="no" title="margin-collapse-flex-grid" src="https://codepen.io/redmaze/embed/ZEVEVVx?default-tab=html%2Cresult" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/redmaze/pen/ZEVEVVx">
  margin-collapse-flex-grid</a> by Mustafa (<a href="https://codepen.io/redmaze">@redmaze</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

Take a look at [codepen above](https://codepen.io/redmaze/pen/ZEVEVVx). Between two adjacent block elements, the margin is collapsed. The margin is calculated as `50px` instead of `70px` (the maximum between collapsed margin).

But if we set the container as `grid` or `flex`. There is no margin collapse. And it doesn't affect the `gap` style. So the final margin calculated above is `20px` (margin-bottom of class blue) + `10px` (margin-top of class red) + `50px` (gap size of container) = `80px` (final margin).

### Further Reading

- [Mastering margin collapsing](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Box_Model/Mastering_margin_collapsing)
