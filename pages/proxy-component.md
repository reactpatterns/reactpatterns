# Proxy Component

A proxy component is a placeholder component that can be rendered to or from another component. In short a proxy component is a reusable component.

For example:

```jsx
import React from 'react'

class Button extends React.Component {
  render() {
    return <button type="button">My Button</button>
  }
}

class App extends React.Component {
  render() {
    return <Button />
  }
}

export default App
```
