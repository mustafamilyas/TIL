# Fix Subpixel Rendering Using JS

### Problem

You have a div that animate transform attribute using percentage value. Sometime the calculation result is a decimal subpixel value, which your screen cannot render correctly.

```

```

### Solution

I have tried several solutions on this [stackoverflow thread](https://stackoverflow.com/questions/27385126/chrome-font-appears-blurry/), but nothing works. The only solution that is working is using JS. The idea is to normalize the value of transform attribute when the animation finish. See below.
