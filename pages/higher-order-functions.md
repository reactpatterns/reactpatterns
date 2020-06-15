# Higher Order Functions

What is Higher Order Functions?

1. A higher order function is a function that takes a function as an argument, or returns a function.

2. Higher order function is in contrast to first order functions, which don’t take a function as an argument or return a function as output.

The below given function can be termed as a Higher Order Function.

```js
// Getting a Specific Getter from Generic get
function get(prop){
  return function(obj){
    return obj[prop]
  }
}

const getName = get("name")
const name = getName({"name": "Jonh"})
console.log(name)
```
