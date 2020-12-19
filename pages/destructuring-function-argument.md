# Destructuring Function Argument

Destructuring can be applied to function arguments that are objects or arrays.

## For example

Without destructuring.

```jsx
function Modal(props) {
  var onClickNext = props.onClickNext
  var step = props.step

  return (
    <div>
      <h1>Step {step} - Name</h1>
      <Button onClick={onClickNext}>Next</Button>
    </div>
  )
}
```

This function expects a single object as an argument and it is destructured into onClickNext and step.

```jsx
function ModalName({ onClickNext, step }) {
  return (
    <div>
      <h1>Step {step} - Name</h1>
      <Button onClick={onClickNext}>Next</Button>
    </div>
  )
}
```
