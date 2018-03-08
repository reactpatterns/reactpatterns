# Component injection

Naming your props is important but instead of calling a function to render, I’d like to propose that, in many cases, you should pass a component.

This allows you to use the more expressive JSX syntax. It’s called "Component Injection" because you pass (or inject) a component into another component.

```
const Hello = ({ name }) => {
  return <div>`hello from ${name}`</div>;
};
```

```
<Foo Hello={Hello} />
```

Things look pretty much the same as in the [Function as prop component](pages/Function-as-prop-component.md "Function as prop component"), except we capitalize `Hello` because convention calls for us to capitalize the first letter of a component name. We also pass in `props`, an object, instead of a single string parameter, but those are the only differences.

And `Foo` component will looks a lot more like a traditional React component.

```
const Foo = ({ Hello }) => {
  return <Hello name="foo" />;
};
```

Now let take a look at a advanced example, altered for Component Injection.

```
render() {
  const { width } = this.state;
  const { Width } = this.props;
  return <Width width={width} />;
}
```

as well as how you use it.

```
<PageWidth Width={DisplayPageWidthText} />
```

```
const DisplayWindowWidthText = ({ width }) => {
  return <div>window is {width}</div>;
};
```

As you can see, the `DisplayPageWidthText` component is "injected" into `PageWidth` as a prop named `Width`.

You could even pass a different component and get a completely different rendered output, thanks to the power of [Render callback](pages/Render-callback.md "Render callback").

```
<PageWidth Width={DisplayDevice} />
```

```
const DisplayDevice = ({ width }) => {
  let device = null;
  if (width <= 480) {
    device = 'mobile';
  } else if (width <= 768) {
    device = 'tablet';
  } else {
    device = 'desktop';
  }
  return <div>you are using a {device}</div>;
};
```