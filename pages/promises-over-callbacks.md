# Promises Over Callbacks

For HTTP Request, our existing solution is to use callbacks.

```jsx
request(url, (error, response) => {
  // handle success or error.
});

doSomethingElse()
```

A few problems exist with callbacks. One is known as [callback hell](http://callbackhell.com "Callback Hell"). A larger problem is decomposition.

The callback pattern require us to specify the task and the callback at the same time. By difference, promises allow us to specify and dispatch the request in one place.

```jsx
promise = fetch(url) // fetch is a replacement for XMLHttpRequest
```

And then add the callback later, and in a different place.

```jsx
promise.then(response => {
  // handle the response
})
```

This also allows us to attach multiple handlers to the same task.

```jsx
promise.then(response => {
  // handle the response.
})

promise.then(response => {
  // do something else with the response.
})
```
