# State hoisting

As the application grows you will realise that some components will need common data or actions in one component may need to cause another component to re-render as well.

Let take a look the example below.

```
// App.js

import React from 'react';
import Header from 'Header';
import List from 'List';

export class App extends React.Component {
  render(){
    return(
      <div>
        <Header/>
        <List/>
      </div>
    );
  }
}
```

```
// Header.js

import React from 'react'

export class Header extends React.Component {
  constructor(props) {
    super(props);
    this.state = {customers: []};
  }

  componentDidMount() {
    const customers = getData(); // this fictional function calls an API
    this.setState({customers});
  }

  render() {
    return(<div>No of Customer: {this.state.customers.length}</div>);
  }
}
```

```
// List.js

import React from 'react';

export class List extends React.Component {
  constructor(props) {
    super(props);
    this.state = {customers: []};
  }

  componentDidMount() {
    const cars = getData(); // this fictional function calls an API
    this.setState({customers});
  }

  render() {
    return this.state.customers.map((car) => {
      return (<div>Customer: {customers.name}</div>)
    });
  }
}
```

As the example above you are encouraged to lift state up, if two components need to act on the same data or need to use the same callback. It mean that you should create a common ancestor in this common ancestor and then use the state to manage all the data and callbacks that children will use in rendering.

```
// App.js

import React from 'react'
import Header from 'Header'
import List from 'List'

export class App extends React.Component {
  constructor(props){
    super(props);
    this.state = {customers: []};
  }

  componentDidMount() {
    const customers = getData(); // this fictional function calls an API
    this.setState({customers});
  }

  render(){
    const {customers} = this.state;

    return(
      <div>
        <Header customers/>
        <List customers/>
      </div>
    );
  }
}
```

```
// Header.js

const Header = ({customers}) => (<div> No of Customer: {customers.length}</div>);

export Header;
```

```
// List.js

const List = ({customers}) => (
  customers.map((customer) => {
    return (<div>Customer: {customer.name}</div>)
  });
)

export List;
```