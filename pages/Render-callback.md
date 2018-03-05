# Render callback

Take a look at the example below. Notice that we create a function `foo` which takes a callback function as a parameter. When we call `foo`, it turns around and “calls back” to the passed-in function.

```
const foo = (hello) => {
  return hello('foo');
};

foo((name) => {
  return `hello from ${name}`;
});

// hello from foo
```

As you can see, `foo` used the callback function to complete a portion of a string. In the React world, a render callback works the same way, but returning a portion of the rendered markup.

Here’s what we would like to use it:

```
const App = () => {
  return (
    <div>
      <FieldItem username='Bunlong'>
        {user => user === null ? <Loading /> : <Profile info={user} />}
      </FieldItem>
    </div>
  );
};
```

`FieldItem` will render either the `Loading` or the `Profile` component, depending on the existence of a `user` property. It also passes down a prop of its own, `username`, that one of these components can consume to make a call

What is interesting here is that `<FieldItem/>` uses a function as a child. Any child component inside it is now free to consume this prop however it needs to, totally decoupled from the parent.

To make it work, the key is to treat `this.props.children` as a function. So in order for the `Profile` component to render whatever it needs to render, it needs to run the callback on the `children` function, passing it the `user` argument it expects. Here’s an example implementation of `Profile`:

```
class FieldItem extends React.Component {
  state = { user: null }

  componentDidMount() {
    // We can make an ajax call here, for e.g.
    setTimeout(() => this.setState({
      user: `I have now fulfilled something for ${this.props.username}`
    }), 1500);
  }

  render() {
    // Render the children with a function using state as the argument
    return this.props.children(this.state.user);
  }
}
```

The key there is the child component rendering `return this.props.children(this.state.user)` with its own state. This means its up to the component to decide how to use the arguments it receives, and the parent component `FieldItem` doesn’t care: it only manages which component to render, in this case.

Looking at `Profile`, since `user` is `null` for 1000ms, the callback receives null as a value for `user`, thus rendering `<Loading />` first. Once we have a `user`, the Profile component will then render. I really enjoy the simplicity and the cleanliness of this approach managing components.

```
// Loading component
const Loading = () => <p>Loading...</p>;

// Profile component
const Profile = (props) => <p>{props.info}</p>;

const App = () => {
  return (
    <div>
      <h3>An application</h3>
      <FieldItem username='magalhini'>
        { user => user === null ? <Loading /> : <Profile info={user} /> }
      </FieldItem>
    </div>
  );
};
  
class FieldItem extends React.Component {
  state = { user: null }
  
  componentDidMount() {
    // We can make an ajax call here, for e.g.
    setTimeout(() => this.setState({
      user: `I have now fulfilled something for ${this.props.username}`
    }), 1500);
  }
  
  render() {
    // Render the children with a function using state as the argument
    return this.props.children(this.state.user);
  }
}
          
ReactDOM.render(<App/>, document.getElementById('app'));
```