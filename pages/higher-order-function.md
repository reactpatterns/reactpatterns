# Higher-Order Function

## What is Higher-Order Function?

Functions that operate on other functions, either by taking them as arguments or by returning them are called higher-order functions.

## For examples

We can have functions that create new functions.

```js
function greaterThan(n) {
  return m => m > n
}

const greaterThan10 = greaterThan(10)

console.log(greaterThan10(11))
// true
```

We can have functions that change other functions.

```js
function noisy(f) {
  return (...args) => {
    console.log("calling with", args)
    const result = f(...args)
    console.log("called with", args, ", returned", result)
    return result
  }
}
noisy(Math.min)(3, 2, 1)
// calling with [3, 2, 1]
// called with [3, 2, 1] , returned 1
```

We can even write functions that provide new types of control flow.

```js
function unless(test, then) {
  if (!test) then()
}

repeat(3, n => {
  unless(n % 2 == 1, () => {
    console.log(n, "is even")
  })
})
// 0 is even
// 2 is even
```

There is a built-in array method, forEach, that provides something like a for/of loop as a higher-order function.

```js
["A", "B"].forEach(l => console.log(l));
// A
// B
```
