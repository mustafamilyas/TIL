# Content Editable Attribute

Sometime, we want to have an input that can be edited by user, but we want to preserve the style of the text. One way to do this, is to swap the element on runtime. But this is not a good solution, because it will cause the element to be re-rendered, which is not good for performance.

Another way to do this is to use `contenteditable` attribute. This attribute will make the element editable, but it will preserve the style of the text.

```html
<div contenteditable="true">This is editable</div>
```

### Gotcha

- One of the great things about input is they can have `placeholder` attribute to provide a clue to the user. But `contenteditable` doesn't have this attribute. Here is one way to solve this problem.

```html
<div contenteditable="true" data-placeholder="This is placeholder"></div>
```

```css
[data-placeholder]:empty::before {
  content: attr(data-placeholder);
  color: gray;
}
```

### Further Reading

- [contenteditable - MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/contenteditable)
