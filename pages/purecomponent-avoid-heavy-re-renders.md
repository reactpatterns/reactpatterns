# Pure Component Avoid Heavy Re-render

`React.PureComponent` is one of the most ways to optimize React applications that is easy and fast to implement. The usage of `React.PureComponent` gives a considerable increase in performance because it reduces the number of render operation in the application.

`PureComponent` changes the life-cycle method `shouldComponentUpdate` and adds some logic to automatically check whether a re-render is required for the component. This allows a PureComponent to call method render only if it detects changes in `state` or `props`, hence, one can change the state in many components without having to write extra checks like:

```jsx
if (this.state.someVal !== computedVal) {
  this.setState({ someVal: computedVal })
}
```

The transition to `PureComponent` is quite simple, if you are aware of peculiarities of the shallowEqual and JS itself. Normally, the migration as simple as changing the base class from.

```jsx
import { Component } from 'react'

export default class MyComponent extends Component {
  render() {
    <SomeComponent someProp={props.someProp} />
  }
}
```

To

```jsx
import { PureComponent } from 'react'

export default class MyComponent extends PureComponent {
  // Won't re-render when the props DONT change
  render() {
    return <SomeComponent someProp={props.someProp}/>
  }
}
```
