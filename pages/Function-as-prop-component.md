# Function as prop component

Exactly passing a render callback function to a component is not the issue. The issue is the [Function as child component](pages/Function-as-child-component.md "Function as child component") implementation chose to use the prop `children`.

So how could you pass a [Render callback](pages/Render-callback.md "Render callback") function to a component in a clean manner?

You would need to name your prop meaningful.

Here’s how you could change the Foo example to pass a function as a prop.

```
<Foo hello={(name) => <div>`hello from ${name}`</div>} />
```

And here’s another example, hello is created outside of the JSX (a better practice).

```
const hello = (name) => {
  return <div>`hello from ${name}`</div>;
};
```

```
<Foo hello={hello} />
```

And this time, Foo makes a lot more sense.

```
const Foo = ({ hello }) => {
  return hello('foo');
};
```

Notice how this is much more descriptive? The code is self-documenting. You can say to yourself, "Foo calls a hello function" instead of "Foo calls something".
