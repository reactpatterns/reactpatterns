# Functional setState (Pass a function to setState)

React has popularized functional programming in JavaScript. So today I reveal to you a new functional gold in React is ***Functional setState***.

Assume that you have a User component as below:

```js
class User {
  state = {
    score : 0,
  }

  render () {
    return (
      <div>This user scored {this.state.score}</div>
    )
  }
}
```

To manage the state, React provides a special method called `setState()`. You use it like as following:

```js
class User {
  ... 

  increaseScore () {
    this.setState({score : this.state.score + 1})
  }

  ...
}
```

How does `setState()` works? You pass it an object containing part(s) of the state you want to update. In other words, the object you pass would have keys corresponding to the keys in the component state, then `setState()` updates or sets the state by merging the object to the state. Thus, "set-State".

Instead of passing an object, you could pass a function to setState as well.

`setState()` also accepts a function. The function accepts the previous state and current props of the component which it uses to calculate and return the next state.

**Usage:**

```js
this.setState(function (state, props) {
 return {
  score: state.score + 1
 }
})
```

Ex:

```js
function increment(state, props) {
  return {
    value: state.value + props.step,
  };
}

function decrement(state, props) {
  return {
    value: state.value - props.step,
  }
}

class Counter extends React.Component {
  state = { value: 0 };

  handleIncrement = () => {
    this.setState(increment);
  }

  handleDecrement = () => {
    this.setState(decrement);
  }

  render() {
    return (
      <div>
        <button onClick={this.handleIncrement}>+</button>
        <h1>{this.state.value}</h1>
        <button onClick={this.handleDecrement}>-</button>
      </div>
    )
  }
}
```
