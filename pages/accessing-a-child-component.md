## Accessing a Child Component

Accessing a child component from the parent. For instance, autofocus an input (controlled by parent component).

Assume that you have a sign-in form, you want to put the cursor in the user name fields once page render.

Let take a look the child component:

```js
class Input extends Component {
  focus() {
    this.el.focus();
  }
  
  render() {
    return (
      <input
        ref={el=> { this.el = el; }}
      />
    );
  }
}
```

An Input component with a `focus()` method that focuses the HTML element.

In the parent component, we can get a reference to the Input component and call its `focus()` method.

```js
class SignInModal extends Component {
  componentDidMount() {
    // Note that when you use ref on a component, it's a reference to 
    // the component (not the underlying element), so you have access to its methods.
    
    this.InputComponent.focus();
  }
  
  render() {
    return (
      <div>
        <label>User name: </label>
        <Input ref={comp => { this.InputComponent = comp; }} />
      </div>
    )
  }
}
```
