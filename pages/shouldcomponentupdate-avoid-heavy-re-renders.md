# shouldComponentUpdate Avoid Heavy re-renders

React component re-render every time the props or state change. So imagine having to render the entire page every time there in an action. That takes a big load on the browser. That's where shouldComponentUpdate comes in, whenever React is rendering the view it checks to see if shouldComponentUpdate is returning false/true. So whenever you have a component that is static let do yourself a favor and return false. Or if not let check to see if the props/state has changed.

Let take a look the below example:

```js
const AutocompleteItem = (props) => {
  const selectedClass = props.selected === true ? "selected" : ""
  var path = parseUri(props.url).path
  path = path.length <= 0 ? props.url : "..." + path

  return (
    <li
      onMouseLeave={props.onMouseLeave}
      className={selectedClass}>
      <i className="ion-ios-eye"
         data-image={props.image}
         data-url={props.url}
         data-title={props.title}
         onClick={props.handlePlanetViewClick} />
      <span
        onMouseEnter={props.onMouseEnter}>
        <div className="dot bg-mint" />
        {path}
      </span>
    </li>
  )
}
```

This component above has no state which causes it to re-render every time. So what we want is to convert it to a regular component and use the function `shouldComponentUpdate`. Then we want to check if the props that we use in this component have change. If there was a change return true else return false. The component becomes:

```js
export default class AutocompleteItem extends React.Component {
  shouldComponentUpdate(nextProps, nextState) {
    return nextProps.url !== this.props.url || nextProps.selected !== this.props.selected
  }

  render() {
    const { props } = this
    const selectedClass = props.selected === true ? "selected" : ""
    let path = parseUri(props.url).path
    path = path.length <= 0 ? props.url : "..." + path

    return (
      <li
        onMouseLeave={props.onMouseLeave}
        className={selectedClass}>
        <i className="ion-ios-eye"
           data-image={props.image}
           data-url={props.url}
           data-title={props.title}
           onClick={props.handlePlanetViewClick} />
        <span
          onMouseEnter={props.onMouseEnter}>
          <div className="dot bg-mint" />
          {path}
        </span>
      </li>
    )
  }
}
```
