# Component Injection

## What is Component Injection?

Passing (or inject) a component into another component it's called Component Injection.

## Example 1

```jsx
const Hello = ({ name }) => {
  return <div>`hello from ${name}`</div>
};
```

```jsx
<Foo Hello={Hello} />
```

It look pretty much the same as in the [function as prop component](/docs/function-as-prop-component "function as prop component"), except the prop we capitalize `Hello` because convention calls for us to capitalize the first letter of a component name. We also pass in `props`, an object, instead of a single string parameter, those are the only differences.

And `Foo` component will looks a lot more like a traditional React component.

```jsx
const Foo = ({ Hello }) => {
  return <Hello name="foo" />
};
```

## Example 2

Let's take a look at a advanced example, altered for component injection.

```jsx
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

So well as how you use it.

```jsx
<PageWidth Width={DisplayPageWidthText} />
```

```jsx
const DisplayWindowWidthText = ({ width }) => {
  return <div>window is {width}</div>
};
```

As you can see, the `DisplayPageWidthText` component is "injected" into `PageWidth` as a prop named `Width`.

You could even pass a different component and get a completely different rendered output, thanks to the power of [render callback](/docs/render-callback "render callback").

```jsx
<PageWidth Width={DisplayDevice} />
```

```jsx
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
