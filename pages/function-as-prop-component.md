# Function as Prop Component

Exactly passing a [Render Callback](./render-callback.md "Render Callback") function to a component is not the issue. The issue is the [Function as Child Component](./function-as-child-component.md "Function as Child Component") implementation chose to use the prop `children`.

So how could you pass a [Render Callback](./render-callback.md "Render Callback") function to a component in a clean manner?

You would need to name your prop meaningful.

Here's how you could change the Foo example to pass a function as a prop:

```js
<Foo hello={(name) => <div>`hello from ${name}`</div>} />
```

And here's another example, hello is created outside of the JSX (a better practice):

```js
const hello = (name) => {
  return <div>`hello from ${name}`</div>
}
```

```js
<Foo hello={hello} />
```

And this time, Foo makes a lot more sense:

```js
const Foo = ({ hello }) => {
  return hello('foo')
}
```

Notice how this is much more descriptive? The code is self-documenting. You can say to yourself, "Foo calls a hello function" instead of "Foo calls something".
