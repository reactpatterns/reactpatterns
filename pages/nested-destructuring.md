# Nested destructuring

Destructuring also applies to objects nested in objects. 

Without destructuring:

```
function setIndexFromRoute(props) {
  const modalList = props.modalList;
  const pathname = props.location.pathname;

  // ...
}
```

Here is an example destructuring the nested props object:

```
function setIndexFromRoute(props) {
  const { modalList, location: { pathname } } = props;

  // ...
}
```