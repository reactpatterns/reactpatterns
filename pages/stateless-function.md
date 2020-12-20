# Stateless Function (Presentational Component)

## What is Stateless Function?

* Stateless function is a way to define React components as a function. Rather than as a class or via `React.createClass`.
* Stateless function does not hold state; just props.

## For examples

Without stateless function, write a presentational component that is just renders props, and doesn't has state.

```js
const UserPassword = React.createClass({
  render() {
    return <p>The user password is: {this.props.userpassword}</p>
  },
})

// OR

class Userpassword extends React.Component {
  render() {
    return <p>The user password is: {this.props.userpassword}</p>
  }
}
```

With stateless function.

```js
const UserPassword = function(props) {
  return <p>The user password is: {this.props.userpassword}</p>
};
```

With stateless function, arrow function, destructuring and implicit return.

```js
const UserPassword = ({userpassword}) => <p>The user password is: {userpassword}</p>
```

Stateless function is great for styling as well.

```js
const PrimaryButton = props => {
  const styles = { background: 'red', color: 'white' }

  return <button {...props} style={styles} />
}
```

Stateless function with event handlers.

```js
const Button = props => {
  const onClick = e => console.log('You clicked me!')

  return <button onClick={onClick}>Click me!</button>
};
```

Stateless function can have defined defaultProps, propTypes.

```js
import PropTypes from 'prop-types'

const UserPassword = props => <p>The user password is: {this.props.userpassword}</p>

UserPassword.propTypes = {
  userpassword: PropTypes.string.isRequired,
}

Username.defaultProps = {
  username: 'Jonh',
}
```

Stateless function can have defined contextTypes (when using context, it's simply passed in as the second argument).

```js
import PropTypes from 'prop-types'

const UserPassword = (props, context) => <p>User password is {context.password}</p>

WowComponent.contextTypes = {
  password: PropTypes.string.isRequired,
}
```
