# Functional stateless component (known as Presentational component)

Functional stateless component (FSC) is a way to define React components as a function, rather than as a class or via `React.createClass`.

Without FSC write a presentational component that is just renders props, and doesn’t has state:

```
const UserPassword = React.createClass({
  render() {
    return <p>The user password is: {this.props.userpassword}</p>;
  },
});

// OR

class Userpassword extends React.Component {
  render() {
    return <p>The user password is: {this.props.userpassword}</p>;
  }
}
```

With FSC:

```
const UserPassword = function(props) {
  return <p>The user password is: {this.props.userpassword}</p>;
};
```

With FSC, arrow function, destructuring and implicit return:

```
const UserPassword = ({ userpassword }) => <p>The user password is: {userpassword}</p>;
```

FSC is great for styling as well:

```
const PrimaryButton = props => {
  const styles = { background: 'red', color: 'white' };

  return <button {...props} style={styles} />;
};
```

FSC with event handlers:

```
const Button = props => {
  const onClick = e => (...);

  return <button onClick={onClick}>Click me!</button>;
};
```

FSC can have defined defaultProps, propTypes:

```
const UserPassword = props => <p>...</p>;

UserPassword.propTypes = {
  userpassword: React.PropTypes.string.isRequired,
};

Username.defaultProps = {
  username: 'Bunlong',
};
```

FSC can have defined contextTypes (when using context, it’s simply passed in as the second argument):

```
const UserPassword = (props, context) => <p>User password is {context.password}</p>;

WowComponent.contextTypes = {
  password: React.PropTypes.string.isRequired,
};
```