# Controlled vs uncontrolled components

## Controlled components

In a controlled component, the form data is handled by the state within the component. The state within the component is the single source of truth for the input elements that are rendered by the component.

A controlled input accepts it's current value as a prop and has a call back to change that value.

```
const Form = () => {
  const [name, setName] = useState('');

  const handleNameChange = (event) => {
    setName(event.target.value);
  };

  return (
    <div>
      <input
        type="text"
        value={name}
        onChange={handleNameChange}
      />
    </div>
  );

}
```

The value of the above input lives in the state and when the value is updated by the user, that change is stored in the state.

This means the data (state) and the UI (inputs) are always in sync and the form component can respond to input changes immediately; for example, by:

- in place feedback, like validation
- disablimng the submit button until all inputs have valid data
- enforcing a specific format, like bank details
