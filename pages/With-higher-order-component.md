# With higher order component

Higher order component are a perfect match for conditional rendering in React. HOC can have multiple use cases. Yet one use case could be to alter the look of a component. To make the use case more specific: it could be to apply a conditional rendering for a component. Let’s have a look at a HOC that either shows a loading indicator or a desired component.

```
// HOC declaration
function withLoadingIndicator(Component) {
  return function EnhancedComponent({ isLoading, ...props }) {
    if (!isLoading) {
      return <Component { ...props } />;
    }

    return <div><p>Loading...</p></div>;
  };
}

// usage
const ListWithLoadingIndicator = withLoadingIndicator(List);

<ListWithLoadingIndicator
  isLoading={props.isLoading}
  list={props.list}
/>
```

In the example, the List component can focus on rendering the list. It doesn’t have to bother with a loading state. Ultimately you could add more HOC to shield away multiple conditional rendering edge cases.