# Button Behavior on Submit Form

When user hit the submit button or press enter key, the form will be submitted (if the inputs are valid). Aside from that, it will also trigger the button's click event. Take a look at code below:

```typescript
import { useState } from "react";
import "./styles.css";

export default function App() {
  const [history, setHistory] = useState([]);
  const appendToHistory = (text: string) => {
    setHistory((prev) => [...prev, text]);
  };
  return (
    <div className="App">
      <form
        onSubmit={(e) => {
          e.preventDefault();
          appendToHistory("form submit");
        }}
      >
        <input
          type="submit"
          value="submit A"
          onClick={() => appendToHistory("submit A on click")}
        />
        <input />
        <input
          type="submit"
          value="submit B"
          onClick={() => appendToHistory("submit B on click")}
        />
        <button onClick={() => appendToHistory("submit C on click")}>
          submit C
        </button>
        <button
          type="button"
          onClick={() => appendToHistory("ordinary button on click")}
        >
          ordinary button
        </button>
      </form>
      <ol>
        {history.map((item) => (
          <li key={item}>{item}</li>
        ))}
      </ol>
    </div>
  );
}
```

You can play around with this code [here](https://codesandbox.io/p/sandbox/crazy-wescoff-535v5g). These are the observed behaviors:

1. if you press enter key on the input text, it will trigger the first submit button's click event and the form's submit event.
2. if you click the submit button, it will trigger it's click event and the form's submit event.
3. if you click the ordinary button, it will trigger it's click event only.

### Read More

- [Form submission algorithm](https://html.spec.whatwg.org/multipage/form-control-infrastructure.html#form-submission-algorithm)
- [How HTMLFormElement works | Stack Overflow](https://stackoverflow.com/questions/63509328/understanding-html-form-element-behavior)
