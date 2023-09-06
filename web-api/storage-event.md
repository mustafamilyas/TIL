# Storage Event

- Part of `window` object that can be used to detect a change in local storage value, but only works when the change is **not** from the current page. The purpose is to **sync** any **changes** on **the same domain**. Other domains will not receive this event.
- how to use

```javascript
window.addEventListener("storage", (event) => {});
document.body.onstorage = (event) => {};
```

- the event parameter contains `key`, `newValue`, `oldValue` (the changed key-value), `storageArea` (the whole object of the local storage), and `url` (the domain that triggers the changes)
- also available on
  - HTMLBodyElement
  - HTMLFrameSetElement
  - SVGSVGElement

### Further Reading

- [Window: storage event](https://developer.mozilla.org/en-US/docs/Web/API/Window/storage_event)
