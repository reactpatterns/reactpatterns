# External templating component

Last but not least there exist external solutions to deal with conditional renderings. They add control components to enable conditional renderings without JavaScript in JSX. Then it is not question anymore on how to use if else in React.

```
<Choose>
  <When condition={isLoading}>
    <div><p>Loading...</p></div>
  </When>
  <Otherwise>
    <div>{list.map(item => <ListItem item={item} />)}</div>
  </Otherwise>
</Choose>
```

Some people use it. Personally I wouldn’t recommend it. JSX allows you to use the powerful set of JavaScript functionalities to handle conditional rendering. There is no need to add templating components to enable conditional rendering. A lot of people consider React including JSX as their library of choice, because they can handle the rendering with pure HTML and JS in JSX.