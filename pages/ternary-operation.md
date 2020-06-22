# Ternary operation

You can make your if-else statement more concise by using a ternary operation.

```
condition ? expr1 : expr2
```

Imagine you have a toggle to switch between two modes, edit and view, in your component. The derived condition is a simple boolean. You can use the boolean to decide which element you want to return.

```
function Item({ item, mode }) {
  const isEditMode = mode === 'EDIT';

  return (
    <div>
      { isEditMode
          ? <ItemEdit item={item} />
          : <ItemView item={item} />
      }
    </div>
  );
}
```

If your blocks in both branches of the ternary operation are getting bigger, you can use parentheses.

```
function Item({ item, mode }) {
  const isEditMode = mode === 'EDIT';

  return (
    <div>
    { isEditMode ? 
      (
        <ItemEdit item={item} />
      ) : 
      (
        <ItemView item={item} />
      )
    }
    </div>
  );
}
```

The ternary operation makes the conditional rendering in React more concise than the if-else statement. It is simple to inline it in your return statement.