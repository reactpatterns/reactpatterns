# Make the API Call in componentDidMount()

You should populate data with AJAX calls in the `componentDidMount` lifecycle method. So you can use setState to update your component when the data is retrieved.

**Class:**

```js
function componentDidMount() {
  fetch(`api/sms`)
    .then(result => {
      const sms = result.data
      console.log("COMPONENT WILL Mount messages : ", sms);
      this.setState({sms: [...sms.content]})
    })
}
```

**Hook:**

```js
useEffect(() => {
  fetch(`api/sms`)
    .then(result => {
      const sms = result.data
      console.log("COMPONENT WILL Mount messages : ", sms);
      setState({sms: [...sms.content]})
    })
}, [])
```
