# Function as Prop Component

Exactly passing a [render callback](/docs/render-callback "render callback") function to a component is not the issue. The issue is the [function as child component](/docs/function-as-child-component "Function as Child Component") implementation chose to use the prop `children`.

So how could you pass a [render callback](/docs/render-callback "render callback") function to a component in a clean manner?

You would need to name your prop meaningful.

Here's how you could change the Foo example to pass a function as a prop:

```jsx
<Foo hello={(name) => <div>`hello from ${name}`</div>} />
```

And here's another example, hello is created outside of the JSX (a better practice):

```jsx
const hello = (name) => {
  return <div>`hello from ${name}`</div>
}
```

```jsx
<Foo hello={hello} />
```

And this time, Foo makes a lot more sense:

```jsx
const Foo = ({ hello }) => {
  return hello('foo')
}
```

Notice how this is much more descriptive? The code is self-documenting. You can say to yourself, "Foo calls a hello function" instead of "Foo calls something".
