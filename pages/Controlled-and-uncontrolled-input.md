# Controlled and uncontrolled input

### Uncontrolled input

Uncontrolled input is like traditional HTML form input:

```
class Form extends Component {
  render() {
    return (
      <div>
        <input type="text" />
      </div>
    );
  }
}
```

They remember what you typed. You can get their value using a `ref`. For example, in onClick handler of a button:

```
class Form extends Component {
  handleSubmitClick = () => {
    const name = this._name.value;
    // do something with `name`
  }

  render() {
    return (
      <div>
        <input type="text" ref={input => this._name = input} />
        <button onClick={this.handleSubmitClick}>Sign up</button>
      </div>
    );
  }
}
```

That is the simplest way to implement the form inputs. It’s not as powerful, though, so let’s see the controlled input.

### Controlled input

A controlled input accepts its current value as a prop, as well as a callback to change that value. You could say it’s a "React way".

```
<input value={someValue} onChange={handleChange} />
```

The value of the input has to live in the state somewhere, the component that renders the input (the form component) saves that in its state:

```
class Form extends Component {
  constructor() {
    super();
    this.state = {
      name: ''
    };
  }

  handleNameChange = (event) => {
    this.setState({ name: event.target.value });
  };

  render() {
    return (
      <div>
        <input
          type="text"
          value={this.state.name}
          onChange={this.handleNameChange}
        />
      </div>
    );
  }
}
```

Whenever you type a new character, `handleNameChange` is called. It takes in the new value of the input and sets it in the state.

![Controlled input](https://github.com/codefacebook/react-patterns/blob/master/static/images/controlled-input-flow.png "Controlled input")

- It starts as an empty string ''.

- You type `a` and `handleNameChange` gets an `a` and calls `setState`. The input is re-rendered to have the value of `a`.

- You type `b` and `handleNameChange` gets the value of `ab` and sets that to the state. The input is re-rendered once more time, now with value `ab`.

Well, This flow kind of pushes the value changes to the form component, so the form component always has the current value of the input, without needing to ask for it.

It means that your data (state) and UI (inputs) are always in sync. The state gives the value to the input, and the input asks the form to change the current value.

***

### Addition

There are many form elements such as checkboxes, radios, selects and textareas.

A form element becomes "controlled" if you set its value via a `prop`.

Each form elements have a different prop for setting that value.

| Element                     | Value Property       | Change Callback | New value in Callback  |
| :-------------------------- | :------------------- | :-------------- | :--------------------- |
| `<input type="text" />`     | value="string"       | onChange        | event.target.value     |
| `<input type="checkbox" />` | checked={boolean}    | onChange        | event.target.checked   |
| `<input type="radio" />`    | checked={boolean}    | onChange        | event.target.checked   |
| `<textarea />`              | value="string"       | onChange        | event.target.value     |
| `<select />`                | value="option value" | onChange        | event.target.value     |

Both the controlled and uncontrolled input have their own merit. Evaluate your specific situation and pick the right one, what works for you is good enough.

| Feature                                   | Uncontrolled       | Controlled         |
| :---------------------------------------- | :----------------- | :----------------- |
| one-time value retrieval (e.g. on submit) | :heavy_check_mark: | :heavy_check_mark: |
| validating on submit                      | :heavy_check_mark: | :heavy_check_mark: |
| instant field validation                  | :x:                | :heavy_check_mark: |
| conditionally disabling submit button     | :x:                | :heavy_check_mark: |
| enforcing input format                    | :x:                | :heavy_check_mark: |
| several inputs for one piece of data      | :x:                | :heavy_check_mark: |
| dynamic inputs                            | :x:                | :heavy_check_mark: |
