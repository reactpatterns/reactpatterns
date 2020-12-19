# Accessing a Child Component

React provide a way to access to a child's DOM node from a parent component by using `Refs`.

For examples:

Assume that you want to put the cursor in the user name fields when the page render.

In child component, we create `Refs` by using `React.createRef()` and then attached to React elements via the `ref` attribute. 

```js
import React from 'react'

class Input extends React.Component {
  constructor(props) {
    super(props)
    // create a ref to store the textInput DOM element
    this.textInput = React.createRef()
  }

  focus() {
    // EXPLANATION: a reference to the node becomes accessible at the current attribute of the ref.
    // make the DOM node focus
    this.textInput.current.focus();
  }
  
  render() {
    return (
      <input
        type="text"
        ref={this.textInput}
      />
    )
  }
}
```

In the parent component, we can get a reference to the Input component and call its `focus()` method.

```js
class SignInModal extends React.Component {
  componentDidMount() {
    // NOTE: when you use ref on a component, it's a reference to 
    // the component (not the underlying element), so you have access to its methods.
    this.InputComponent.focus();
  }
  
  render() {
    return (
      <div>
        <label>User name: </label>
        {/* we use "callback refs" to get the React component instance */}
        <Input ref={component => {this.InputComponent = component }} />
      </div>
    )
  }
}
```
