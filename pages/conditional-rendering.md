# Conditional Rendering

In JavaScript you should be familiar with if-else or switch case statements. You can use it in JSX as well, since JSX only mixes HTML and JavaScript.

But what is conditional rendering in React? In a conditional render a component decides based on one or several conditions which elements it will return. For instance, it can either return a list of items or a message that says “Sorry, the list is empty”. When a component has conditional rendering, the instance of the rendered component can have different looks.

Here is the list of options for conditional rendering:

* [If else](If-else.md "If else")

* [Ternary operation](Ternary-operation.md "Ternary operation")

* [Logical && operator](Logical-and-operator.md "Logical && operator")

* [Switch case operator](Switch-case-operator.md "Switch case operator")

* [Conditional rendering with enum](Conditional-rendering-with-enum.md "Conditional rendering with enum")

* [Multi-Level conditional rendering](Multi-level-conditional-rendering.md "Multi-Level conditional rendering")

* [With higher order component](With-higher-order-component.md "With higher order component")

* [External templating component](External-templating-component.md "External templating component")

When to use which type of conditional render?

* [If else](If-else.md "If else")

   * is the most basic conditional rendering

   * beginner friendly

   * use if to opt-out early from a render method by returning null

* [Ternary operation](Ternary-operation.md "Ternary operation")

   * use it over an if-else statement

   * it is more concise than if-else

* [Logical && operator](Logical-and-operator.md "Logical && operator")

   * use it when one side of the ternary operation would return null

   * but be careful that you don’t run into bugs when using multiple conditions

* [Switch case operator](Switch-case-operator.md "Switch case operator")

   * verbose

   * can only be inlined with self invoking function

   * avoid it, use enums instead

* [Conditional rendering with enum](Conditional-rendering-with-enum.md "Conditional rendering with enum")

   * perfect to map different states

   * perfect to map more than one condition

* [Multi-Level conditional rendering](Multi-level-conditional-rendering.md "Multi-Level conditional rendering")

   * avoid them for the sake of readability

   * split up components into more lightweight components with their own simple conditional rendering

   * use HOC

* [With higher order component](With-higher-order-component.md "With higher order component")

   * use them to shield away conditional rendering

   * component can focus on their main purpose

* [External templating component](External-templating-component.md "External templating component")

   * avoid them and be comfortable with JSX and JavaScript
