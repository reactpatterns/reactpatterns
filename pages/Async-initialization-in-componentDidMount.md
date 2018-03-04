# Async initialization in componentDidMount()

You should avoid async initialization in componentWillMount(), componentWillMount() is called before render() that why setting state in this method will not trigger render() method.

You should make async calls for component initialization in componentDidMount() instead of componentWillMount()

```
function componentDidMount() {
  axios.get(`api/sms`)
    .then((result) => {
      const sms = result.data
      console.log("COMPONENT WILL Mount messages : ", sms);
      this.setState({
        sms: [...sms.content]
      })
    })
}
```