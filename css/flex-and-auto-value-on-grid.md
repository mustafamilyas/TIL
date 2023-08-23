# Flex and Auto Values in Grid Layout

Both of these values will occupy the remaining space after other values have been calculated. However, there are some similarities and differences as demonstrated in [my experiment](https://codepen.io/redmaze/pen/BavNdPa).

1. If the grid consists of either `fr` or `auto`, but not both, it will take up all the remaining space.

2. When the grid consists of both `fr` and `auto` values, it calculates the minimum size of all `auto` grids and then assigns the remaining space to the `fr` grid.

3. The `auto` value will only take up the remaining space if there is no `fr` grid present.

4. In cases where there are multiple `auto` values but no `fr` value, it calculates the minimum size of each element and then distributes the remaining space equally between the elements. For example:

   ```html
   <div class="container">
     <div class="child">
       <div class="element-a">child1</div>
     </div>
     <div class="child">
       <div class="element-b">child2</div>
     </div>
   </div>
   ```

   ```css
   .container {
     width: 1000px;
     grid-template-columns: auto auto;
   }
   .element-a {
     width: 300px; /* resulting width: 600px */
   }
   .element-b {
     width: 100px; /* resulting width: 400px */
   }
   ```

5. When there are multiple `fr` values but no `auto` value, the remaining space is distributed according to the specified flex value. For instance:

   ```html
   <div class="container">
     <div class="child">
       <div class="element-a">child1</div>
     </div>
     <div class="child">
       <div class="element-b">child2</div>
     </div>
   </div>
   ```

   ```css
   .container {
     width: 1000px;
     grid-template-columns: 1fr 1fr;
   }
   .element-a {
     width: 300px; /* resulting width: 500px */
   }
   .element-b {
     width: 100px; /* resulting width: 500px */
   }
   ```

6. If the minimum width of children exceeds the value of the flex factor `fr`, then the width of that particular `fr` will be that minimum width. For example:

   ```html
   <div class="container">
     <div class="child">
       <div class="element-a">child1</div>
     </div>
     <div class="child">
       <div class="element-b">child2</div>
     </div>
   </div>
   ```

   ```css
   .container {
     width: 1000px;
     grid-template-columns: 1fr 1fr;
   }
   .element-a {
     width: 600px;
     /* initial distribution is 500px, but because the minimum width of the content exceeds that, the final width value also changes */
     /* resulting width: 600px */
   }
   .element-b {
     width: 100px; /* resulting width: 400px */
   }
   ```
