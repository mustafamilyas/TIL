# Add Zoom & Pan Functionality on D3.js

There are 4 steps

1. Init the zoom functionality from d3.js

```javascript
const zoom = d3.zoom().scaleExtent([0.25, 10]);
```

`zoom()` will create a new zoom behavior and
`scaleExtent()` will limit how large and small your scale factor by `[min, max]`. If you don't want to limit the scale factor, you can omit `scaleExtent()`

2. Add zoom behavior to svg element

```javascript
const svg = d3.create("svg").call(zoom);
// other svg attribute configuration
```

3. Group that element that you want to be included in the zoom functionality. Instead of this.

```javascript
const svg = d3.create("svg");
// other svg attribute configuration

const node = svg.append("circle");
// other node attribute configuration
// or maybe other children
```

You need to wrap your zoom zone using group tag (`<g/>`).

```javascript
const svg = d3.create("svg");
// other svg attribute configuration

// wrapper element
const group = svg.append("g");
// call using wrapper instead of svg
const node = group.append("circle");
```

4. Add zoom handler on the zoom zone wrapper element.

```javascript
zoom.on("zoom", handleZoom);

function handleZoom(e) {
  group.attr("transform", e.transform);
}
```
