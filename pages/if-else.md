# If Else

The easiest way to have a conditional rendering is to use an `if-else` in React render method.

Imagine you don't want to render your component, because it doesn't have the necessary props. For instance, a `List` component shouldn't render the list when there is no list of items. You can use an if statement to return earlier from the render lifecycle.

```jsx
function List({ list }) {
  if (!list) {
    return null
  }

  return (
    <div>
      {list.map(item => <ListItem item={item} />)}
    </div>
  )
}
```

A component that returns null will render nothing. However, you might want to show a text when a list is empty to give your app user some feedback for a better user experience.

```jsx
function List({ list }) {
  if (!list) {
    return null
  }

  if (!list.length) {
    return <p>Sorry, the list is empty.</p>
  } else {
    return (
      <div>
        {list.map(item => <ListItem item={item} />)}
      </div>
    )
  }
}
```

The List renders either nothing, a text or the list of items. The `if-else` statement is the most basic option to have a conditional rendering in React.
