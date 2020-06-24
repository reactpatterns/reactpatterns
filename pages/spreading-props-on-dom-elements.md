# Spreading props on DOM elements

Well, we usually spread the properties to the elements to avoid writing every single one manually.

```js
<Component {...props} />
```

This works very well.

However, when we spread props into a DOM element, we run the risk of adding unknown HTML attributes, which is a bad pratice.

To see the warning in the console, a basic operation we can do is render the following component.

```js
const Spread = () => <div foo="bar" />
```

The message we get looks like the following:

```
Unknown props `foo` on <div> tag. Remove this prop from the element
```

Because the foo property is not valid for a div element.

In this case, as we said, it's easy to figure out which attribute we are passing and remove it but, if we use the spread operator, as in the following.

```js
const Spread = props => <div {...props} />
```

We can't control which properties are passed from the parent.

If we use the component in this way:

```js
<Spread className="foo" />
```

There are no issues.
