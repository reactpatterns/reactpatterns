# Nested Destructuring

Destructuring also applies to objects nested in objects. 

## For example

Without destructuring:

```jsx
function setIndexFromRoute(props) {
  const modalList = props.modalList
  const pathname = props.location.pathname

  // ...
}
```

Destructuring the nested props object.

```jsx
function setIndexFromRoute(props) {
  const { modalList, location: { pathname } } = props

  // ...
}
```
