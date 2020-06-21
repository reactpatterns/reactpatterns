# Component Injection

Passing (or inject) a component into another component it's called Component Injection.

Example 1:

```js
const Hello = ({ name }) => {
  return <div>`hello from ${name}`</div>
};
```

```js
<Foo Hello={Hello} />
```

It look pretty much the same as in the [Function as Prop Component](./function-as-prop-component.md "Function as Prop Component"), except the prop we capitalize `Hello` because convention calls for us to capitalize the first letter of a component name. We also pass in `props`, an object, instead of a single string parameter, those are the only differences.

And `Foo` component will looks a lot more like a traditional React component:

```js
const Foo = ({ Hello }) => {
  return <Hello name="foo" />
};
```

Example 2:

Let's take a look at a advanced example, altered for Component Injection:

```js
import React from 'react'

export default class PageWidth extends React.Component {
  state = { width: 100 }

  render() {
    const { width } = this.state
    const { Width } = this.props

    return <Width width={width} />
  }
}
```

Ss well as how you use it.

```js
<PageWidth Width={DisplayPageWidthText} />
```

```js
const DisplayWindowWidthText = ({ width }) => {
  return <div>window is {width}</div>
};
```

As you can see, the `DisplayPageWidthText` component is "injected" into `PageWidth` as a prop named `Width`.

You could even pass a different component and get a completely different rendered output, thanks to the power of [Render Callback](./render-callback.md "Render Callback"):

```js
<PageWidth Width={DisplayDevice} />
```

```js
const DisplayDevice = ({ width }) => {
  let device = null
  if (width <= 480) {
    device = 'mobile'
  } else if (width <= 768) {
    device = 'tablet'
  } else {
    device = 'desktop'
  }
  return <div>you are using a {device}</div>
}
```
