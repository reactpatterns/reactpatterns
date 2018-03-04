# JSX spread attributes

Spread Attributes is a JSX feature, it’s a syntactic for passing all of an object’s properties as JSX attributes.

If you know all the properties that you want to place on a component ahead of time, it is easy to use JSX.

```
var component = <Component foo={x} bar={y} />;
```

If you don't know which properties you want to set, you might be tempted to add them onto the object later.

```
var component = <Component />;
component.props.foo = x; // bad
component.props.bar = y; // also bad
```

Now you can use a new feature of JSX called spread attributes:

```
var props = {};
props.foo = x;
props.bar = y;
var component = <Component {...props} />;
```

The properties of the object that you pass in are copied onto the component's props.

You can use this multiple times or combine it with other attributes. The specification order is important. Later attributes override previous ones.

```
var props = { foo: 'default' };
var component = <Component {...props} foo={'override'} />;
console.log(component.props.foo); // 'override'
```