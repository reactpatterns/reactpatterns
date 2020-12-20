# JSX Spread Attributes

## What is JSX Spread Attributes?

Spread attributes is a JSX feature, it's a syntax for passing all of an object's properties as JSX attributes.

## For examples

If you know all the properties that you want to place on a component ahead of time, it is easy to use JSX.

```js
const component = <Component foo={x} bar={y} />
```

If you don't know which properties you want to set, you might be tempted to add them onto the object later.

```js
var component = <Component />;
component.props.foo = x // bad
component.props.bar = y // also bad
```

Now you can use a new feature of JSX called spread attributes.

```js
let props = {}
props.foo = x
props.bar = y

const component = <Component {...props} />
```

The properties of the object that you pass in are copied onto the component's props. You can use this multiple times or combine it with other attributes. The specification order is important. Later attributes override previous ones.

```js
let props = { foo: 'default' }
const component = <Component {...props} foo={'override'} />
console.log(component.props.foo) // 'override'
```
