# Detect When Sticky Position Applied

When you want to detect when the sticky position is applied, you can use `IntersectionObserver`. Here is an example using `React`:

```jsx
import React, { useEffect, useRef } from "react";

export const Sticky = () => {
  const ref = useRef < HTMLDivElement > null;

  useEffect(() => {
    let el = ref.current;
    const observer = new IntersectionObserver(
      ([e]) => {
        // toggle pinned class when the element intersects with the viewport/container
        e.target.classList.toggle("pinned", e.intersectionRatio < 1);
      },
      { threshold: [1] }
    );
    if (el) {
      observer.observe(el);
    }

    return () => {
      if (el) {
        observer.unobserve(el);
      }
    };
  }, []);
  return (
    <div className="container">
      <div className="child" ref={ref}>
        Sticky
      </div>
    </div>
  );
};
```

```css
.container {
  height: 200vh;
}

.myElement {
  position: sticky;
  /*
    the trick is to set the top value to -1px, so the element will be considered intersecting with the viewport/container
   */
  top: -1px;
}

/* styles for when the header is in sticky mode */
.myElement.is-pinned {
  color: red;
}
```

### Further Reading

- [How to Detect When a Sticky Element Gets Pinned
  ](https://css-tricks.com/how-to-detect-when-a-sticky-element-gets-pinned/)
