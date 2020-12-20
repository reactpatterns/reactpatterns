# Logical && Operator

It happens often that you want to render either an element or nothing. You could have a `LoadingIndicator` component that returns a loading text or nothing. You can do it in JSX with an if statement or ternary operation.

```jsx
function LoadingIndicator({ isLoading }) {
  if (isLoading) {
    return (
      <div>
        <p>Loading...</p>
      </div>
    )
  } else {
    return null
  }
}

function LoadingIndicator({ isLoading }) {
  return (
    <div>
      { isLoading
          ? <p>Loading...</p>
          : null
      }
    </div>
  )
}
```

But there is an alternative way that omits the necessity to return null. The logical `&&` operator helps you to make conditions that would return null more concise.

How does it work? In JavaScript a `true && 'Hello World'` always evaluates to `Hello World` and a `false && 'Hello World'` always evaluates to false.

```jsx
const result = true && 'Hello World'
console.log(result)
// Hello World

const result = false && 'Hello World'
console.log(result)
// false
```

In React you can make use of that behaviour. If the condition is true, the expression after the logical `&&` operator will be the output. If the condition is false, React ignores and skips the expression.

```jsx
function LoadingIndicator({ isLoading }) {
  return (
    <div>
      { isLoading && <p>Loading...</p> }
    </div>
  )
}
```

That's your way to go when you want to return an element or nothing. It makes it even more concise than a ternary operation when you would return null for a condition.
