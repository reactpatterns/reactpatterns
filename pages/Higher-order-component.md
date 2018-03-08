# Higher order component - Props proxy

Higher order components in React follow the important concept of Composition. In React, Large components can be composed of smaller components to implement separation of concerns. Any React App can be seen as a composition of Hierarchical Components.

Higher order component in ReactJS is similar to HOF (Higher order function) and can be defined as any function that takes a component as argument and returns another component. The returned component will contain/compose the initial argument passed in the argument to the function.

```
export default HOC(ComposedComponent) {
  return class WrapperComponent extends React.Component {
    componentDidMount(){
      this.newProps = transformationFunc(this.props);
    }
    
    render(){
      <ComposedComponent {...this.props} {...this.newProps} />
    }
  }
}
```

In the above code, we have created a function that takes a component to be composed and returns us a WrapperComponent which includes the ComposedComponent in its render method. The HOC/WrapperComponent can add new props or modify the existing props also. It can also get hooks to the lifecycle methods of the ComposedComponents. The props are passed as it is using the ES6 spread operator.
