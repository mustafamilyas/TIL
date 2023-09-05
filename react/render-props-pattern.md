# Render Props Pattern

Render props pattern is useful to reuse component logic while customizing the looks of your UI. Suppose you have `<Select />` and want to give the user UI the power to customize the looks of their options, this pattern might be helpful to you.

The key to this pattern is to have a prop(s) that will render `ReactNode`. Usually in the form of a function, so that user can get some context for their rendering.

```typescript
interface Props<T> {
  options: T[];
  idSelector?: T => string | number
  // render props, with the individual data and index as the context
  renderItem?: (T, index) => ReactNode;
}
const Select: FC<Props> = ({ options, renderItem }) => {
  // some logic
  return (
    //...
    <ol className="items">
      {options.map((option, index) => (
        <li key={idSelector ? idSelector(option): option}>
            {renderItem ? renderItem(option, index) : option}
        </li>
      ))}
    </ol>
    //...
  );
};

const UI = () => {
    const options = ['Smile', 'Sad']
    return (
        <Select
            options={options}
            renderItem={(option, index) => (
                <span>{index}.{option}</span>
            )}
        />
    )
}
```

Sometimes, we don't need the context, you can just pass the component as props.

```typescript
interface Props
  extends DetailedHTMLProps<
    ButtonHTMLAttributes<HTMLButtonElement>,
    HTMLButtonElement
  > {
  iconStart?: ReactNode;
  iconEnd?: ReactNode;
}
const Button = ({ iconStart, iconEnd, children, ...props }) => {
  return (
    <button {...props}>
      {iconStart || null}
      {children}
      {iconEnd || null}
    </button>
  );
};
```
