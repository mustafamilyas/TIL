# Selection

The first thing we need to do when interacting with d3 is select the element we want to manipulate. In d3 there are two ways: `select` and `selectAll`. These functions act almost similarly with the `document` API counterpart which is `querySelector` and `querySelectorAll`.

```javascript
const elD3 = d3.select("#el");
const elDOM = document.querySelector("#el");
//Both of these will return the first element matches with the valid selector (#el)

const elD3 = d3.selectAll("div.test");
const elDOM = document.querySelectorAll("div.test");
//Both of these will return all of the elements that match with the valid selector (div.test)
```

The difference lies in two things. The first one is the returned value of d3 already adjusted for d3 manipulation. And the second thing is you can also pass DOM object/element to `select` / `selectAll` whereas in `querySelector` / `querySelectorAll` you can't.

```javascript
const elDOM = document.querySelector("#el");
const elD3 = d3.select(elDOM);
```

Here is the example of the returned value of d3 select.

```
{
    "_groups": [
        [
            {} // the selected dom element
        ],
        [
            {} // the selected dom element
        ],
    ],
    "_parents": [
        {} // the parent of the selected element
    ]
}
// If no match
{
    "_groups": [
        [null]
    ],
    "_parents": [
        {} // the parent of the selected element, in case of null, it is HTML
    ]
}
```
