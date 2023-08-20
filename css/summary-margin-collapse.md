# Summary of Margin Collapse

All of the below cases assume there is no element in the middle of the adjacent sibling and the container doesn't display as flex or grid.

1. If the adjacent siblings have **negative** margins, the margin will collapse and the calculated margin between both of those elements is the **lowest** margin.

   ```html
   <div class="sibling-a">sibling a</div>
   <div class="sibling-b">sibling b</div>
   ```

   ```css
   .sibling-a {
     margin-bottom: -60px; /* the chosen margin */
   }
   .sibling-b {
     margin-top: -20px;
   }
   ```

2. If the adjacent siblings have **positive** margins, the margin will collapse and the calculated margin between both of those elements is the **highest** margin.

   ```html
   <div class="sibling-a">sibling a</div>
   <div class="sibling-b">sibling b</div>
   ```

   ```css
   .sibling-a {
     margin-bottom: 20px;
   }
   .sibling-b {
     margin-top: 60px; /* the chosen margin */
   }
   ```

3. If one sibling has a negative margin and the other has a positive margin, the margin **won't** collapse and the calculated margin between both of those elements is the **sum of both margins**.
   ```html
   <div class="sibling-a">sibling a</div>
   <div class="sibling-b">sibling b</div>
   ```
   ```css
   .sibling-a {
     margin-bottom: 20px;
   }
   .sibling-b {
     margin-top: -60px;
   }
   /* the calculated margin is 20px - 60px = 40px */
   ```
