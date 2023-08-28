# Accent Color on Input

To change the color of accent on input there are two ways. The demo can be found [here](https://codepen.io/redmaze/pen/PoXZWxJ).

1. Accent Color
   only apply to on below element

   ```html
   <input type="checkbox" style="accent-color: red" checked />
   <input type="radio" style="accent-color: orange" checked />
   <input type="range" style="accent-color: yellow" />
   <progress style="accent-color: black"></progress>
   ```

   You may notice that on the range element, the track becomes black. This depends on the browser implementation. But in chrome, the light accent color will make the track color to be black, but the dark color will make the track color to be white. This apply to `<input type="range"/>` & `<progress/>`

2. Caret Color
   When you want to style the accent color of text type input or those that have `contenteditable` input, then you can use `caret-color`
   ```html
   <input style="caret-color: blue" />
   <textarea style="caret-color: orange">test</textarea>
   <p contenteditable style="caret-color: red">
     This paragraph can be edited, and its caret has a custom color as well!
   </p>
   ```
