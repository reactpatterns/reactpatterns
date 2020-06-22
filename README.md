<p align="center">
  ⭐️ If you like reactpatterns, give it a star! ⭐️
</p>

<img src="https://github.com/codefacebook/react-patterns/blob/master/static/images/reactpatterns.png" align="right" />

# React Patterns

> A curated list of React Patterns

React patterns & techniques to use in development for React Developer.

## Patterns

* [Proxy Component](pages/proxy-component.md "Proxy Component")

* [Make the API Call in componentDidMount()](pages/make-the-api-call-in-componentdidmount.md "Make the API Call in componentDidMount()")

* [Stateless Function (Presentational Component)](pages/stateless-function.md "Stateless Function (Presentational Component)")

* [Functional setState (Pass a function to setState)](pages/functional-setstate.md "Functional setState (Pass a function to setState)")

* [Higher-Order Functions](pages/higher-order-functions.md "Higher-Order Functions")

* [Higher-Order Components](pages/higher-order-components.md "Higher-Order Components")

* [Accessing a Child Component](pages/accessing-a-child-component.md "Accessing a Child Component")

* [JSX Spread Attributes](pages/jsx-spread-attributes.md "JSX Spread Attributes")

* [Render Callback](pages/render-callback.md "Render Callback")

* [Function as Child Component](pages/function-as-child-component.md "Function as Child Component")

* [Function as Prop Component](pages/function-as-prop-component.md "Function as Prop Component")

* [Component Injection](pages/component-injection.md "Component Injection")

<!-- * [Conditional rendering](pages/conditional-rendering.md "Conditional rendering") -->

* Conditional Rendering
  * [if else](pages/if-else.md "if else")
    * is the most basic conditional rendering
    * beginner friendly
    * use if to opt-out early from a render method by returning null
  * [ternary operation](ternary-operation.md "ternary operation")
    * use it over an if-else statement
    * it is more concise than if-else
  * [logical && operator](logical-and-operator.md "logical && operator")
    * use it when one side of the ternary operation would return null
    * but be careful that you don’t run into bugs when using multiple conditions
  * [switch case operator](switch-case-operator.md "switch case operator")
    * verbose
    * can only be inlined with self invoking function
    * avoid it, use enums instead
  * [conditional rendering with enum](conditional-rendering-with-enum.md "conditional rendering with enum")
    * perfect to map different states
    * perfect to map more than one condition
  * [multi-level conditional rendering](multi-level-conditional-rendering.md "multi-level conditional rendering")
    * avoid them for the sake of readability
    * split up components into more lightweight components with their own simple conditional rendering
    * use HOC
  * [with higher order component](with-higher-order-component.md "with higher order component")
    * use them to shield away conditional rendering
    * component can focus on their main purpose
  * [external templating component](external-templating-component.md "external templating component")
    * avoid them and be comfortable with JSX and JavaScript

* [Destructuring](pages/Destructuring.md "Destructuring")

* [Destructuring function arguments](pages/Destructuring-function-arguments.md "Destructuring function arguments")

* [Nested destructuring](pages/Nested-destructuring.md "Nested destructuring")

* [Destructuring rest/spread operator](pages/Destructuring-rest-and-spread-operator.md "Destructuring rest/spread operator")

* [Promises over Callbacks](pages/Promises-over-callbacks.md "Promises over Callbacks")

* [Container component (known as Stateful component)](pages/Container-component.md "Container component (known as Stateful component)")

* [State hoisting](pages/State-hoisting.md "State hoisting")

* [shouldComponentUpdate avoid heavy re-renders](pages/shouldComponentUpdate-avoid-heavy-re-renders.md "shouldComponentUpdate avoid heavy re-renders")

* [Controlled and uncontrolled input](pages/Controlled-and-uncontrolled-input.md "Controlled and uncontrolled input")

* [PureComponent avoid heavy re-renders](pages/PureComponent-avoid-heavy-re-renders.md "PureComponent avoid heavy re-renders")

## Anti Patterns

* [Initializing the state Using props is an Anti-Patterns](pages/Props-in-initial-state-is-an-anti-patterns.md "Props in Initial State is an Anti-Patterns")

* [Using Indexes as a Key is an anti-patterns](pages/Indexes-as-a-key-is-an-anti-patterns.md "Indexes as a key is an anti-patterns")

* [Spreading props on DOM elements is an anti-patterns](pages/Spreading-props-on-DOM-elements-is-an-anti-patterns.md "Spreading props on DOM elements is an anti-patterns")

* Mutating the state

## Contributing

We'd love to have your helping hand on contributions to `reactpatterns` by forking and sending a pull request!

Your contributions are heartily ♡ welcome, recognized and appreciated. (✿◠‿◠)

## License

The MIT License [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)


<!-- =============== -->
<!-- 
callback-ref => https://reactjs.org/docs/refs-and-the-dom.html#callback-refs 

functional-setstate

-->
<!-- =============== -->
