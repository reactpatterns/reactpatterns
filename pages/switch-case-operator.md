# Switch Case Operator

Now there might be cases where you have multiple conditional renderings. The conditional rendering could apply based on different states.

Let's imagine a notification component that can render an error, warning or info component based on the input state. You can use a switch case operator to handle the conditional rendering of these multiple states.

```jsx
function Notification({ text, state }) {
  switch(state) {
    case 'info':
      return <Info text={text} />
    case 'warning':
      return <Warning text={text} />
    case 'error':
      return <Error text={text} />
    default:
      return null
  }
}
```

Please note that you always have to use the `default` for the switch case operator. In React a component has always to return an element or `null`.

As a little information​, when a component has a conditional rendering based on a state, it makes sense to describe the interface of the component with `React.PropTypes`.

```jsx
function Notification({ text, state }) {
  switch(state) {
    case 'info':
      return <Info text={text} />
    case 'warning':
      return <Warning text={text} />
    case 'error':
      return <Error text={text} />
    default:
      return null
  }
}

Notification.propTypes = {
  text: React.PropTypes.string,
  state: React.PropTypes.oneOf(['info', 'warning', 'error'])
}
```

Now you have one generic component to show different kinds of notifications. Based on the state prop the component could have different looks. An error should be red, a warning should be yellow and an info should be blue.

An alternative way would be to inline the switch case. Therefore you would need a self invoking JavaScript function.

```jsx
function Notification({ text, state }) {
  return (
    <div>
      {(() => {
        switch(state) {
          case 'info':
            return <Info text={text} />
          case 'warning':
            return <Warning text={text} />
          case 'error':
            return <Error text={text} />
          default:
            return null
        }
      })()}
    </div>
  )
}
```
