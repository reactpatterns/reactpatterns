# Higher order function

Functions that operate on other functions, either by taking them as arguments or by returning them, are called higher-order functions. 

Functions and they take other functions as arguments and operate on them. Also, the second candidate for Higher Order Functions are Closures which return any function. The below given function can be termed as a Higher Order Function.

```
// Getting a Specific Getter from Generic get
function get(prop){
  return function(obj){
    return obj[prop];
  }
}

let getName = get("name");
let name = getName({"name": "Rahat"});
console.log(name);
```