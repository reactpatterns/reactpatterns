# Make the API Call in componentDidMount()

You should populate data with AJAX calls in the `componentDidMount` lifecycle method. So you can use setState to update your component when the data is retrieved.

For example using Class:

```jsx
function componentDidMount() {
  fetch('api/sms')
    .then(result => {
      const sms = result.data
      console.log('COMPONENT WILL Mount messages : ', sms)
      this.setState({sms: [...sms.content]})
    })
}
```

For example using Hook:

```jsx
useEffect(() => {
  fetch('api/sms')
    .then(result => {
      const sms = result.data
      console.log('COMPONENT WILL Mount messages : ', sms)
      this.setState({sms: [...sms.content]})
    })
}, [])
```
