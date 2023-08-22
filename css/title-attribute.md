# Title Attribute Behavior

- <span title="can be applied to all elements">a global attribute</span>, which mean can be applied to all elements.
- It is useful to show additional information related to the element.
- It is a natively supported tooltip. Unlike a custom tooltip, `title` isn't bound to the stacking context of the element.
- Can't be styled.
- Support multiline text using ` U+000A LINE FEED (LF)`
- Title attribute inherited to the children, but can be replaced if the children also add `title` attribute.
  ```
  <p title="parent tooltip">
      title attribute is a natively <span title="it is cool">supported tooltip</span>
  </p>
  ```
  hover below
    <p title="parent tooltip">title attribute is a natively <span title="it is cool">supported tooltip</span></p>
- If you want to omit the children from the tooltip, you can set the `title` into an empty string, but you need to move away the mouse to clear the tooltip.
  ```
  <p title="parent tooltip">
      title attribute is a natively <span title="">supported tooltip</span>
  </p>
  ```
  hover below
    <p title="parent tooltip">title attribute is a natively <span title="">supported tooltip</span></p>
- It is [not that good for accessibility](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/title#accessibility_concerns) due to browser support.
