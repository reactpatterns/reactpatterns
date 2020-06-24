# Destructuring

Destructuring shown assigns properties of an object to variables of the same name. There is also a longhand syntax that allows you to assign to variables of different names. 

Destructuring works with nested objects, with arrays, and can be used in variable declarations, function return values and function arguments.

Without destructuring:

```
class Modals extends Component {
  render() {
    const modalList = this.props.modalList;
    const currIndex = this.state.currIndex;
    const showModal = this.state.showModal;

    // ...
  }
}
```

Destructuring the objects this.props and this.state:

```
class ChainedModals extends Component {
  render() {
    const { modalList } = this.props;
    const { currIndex, showModal } = this.state;
    
    // ...
  }
}
```