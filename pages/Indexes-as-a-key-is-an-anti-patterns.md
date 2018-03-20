# Indexes as a key is an anti-patterns

Keys should be unique so that React can keep a better track of elements.

Assume you use index of an item as its key when render a list as below:

```
{todos.map((todo, index) =>
  <Todo
    {...todo}
    key={index}
  />
)}
```

A key is the only thing React uses to identify DOM elements. What going on if you push an item to the list or remove items in the middle, If the key is same as before React assumes that the DOM element represents the same component as before.

The better way:

Each items should have a permanent and unique property. It should be assigned when the item is created. Then we can use it the following way.

```
{todos.map((todo) =>
  <Todo 
    {...todo}
    key={todo.id} 
  />
)}
```