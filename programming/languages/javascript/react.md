# React

React is a JaveScript library for building responsive UIs.

## Components

[React components](https://reactjs.org/docs/components-and-props.html) are reusable pieces of code that allow us to split the UI into independent pieces.

Components can be written as regular JS functions or as classes.

### Functional Components

Functional components are regular JS functions that take a `props` parameter. `props` is an object containing properties that are passed to the component.

Example of a functional component:

```
function Person(props) {
    return <p>Hello {props.lastName}!</p>;
}
```

### Class Components

Class components are ES6 classes that extend `React.Component`. They are able to hold state and require a `render()` function to display.

Similar to functional components, class components make use of a `props` object. In this case, `props` is a member of the class rather than a function parameter.

Example of a class component:

```
class Person extends React.Component {
    render() {
        return <p>Hello {this.props.lastName}</p>
    }
}
```

### When to Use Functional vs. Class Components

If a component is just taking in some props and rendering, then it's a good idea to use go functional. If it needs more functionality or has to maintain state, a class is the better options.

NOTE: As of React 16.8, this is no longer accurate. Much of the functionality of class components can now be achieved in functional components using [hooks](https://reactjs.org/docs/hooks-intro.html). Because I have yet to learn about them, I will not write an explanation here and will update this section at a later date.

## Lifecycles

The lifecycle of a component is the sequence of stages it goes through during its time in the DOM tree. This includes things like the time it is created, destroyed, or updated.

### Lifecycle Methods

Lifecycle methods are special methods in React that run during different stages of a component's lifecycle. Examples of lifecycle methods are listed below.

Note that lifecycle methods can only be used in class components.

- Common lifecycle methods
  - `Render()`
    - Contains logic that the component should display on-screen
    - This is the only required method within a class component
    - Has to be a pure function
  - `ComponentDidMount()`
    - Runs when a component is mounted (added to the DOM tree)
    - This is often used for things like connecting to APIs, setting timers, and adding event listeners
  - `ComponentDidUpdate()`
    - Runs each time a component is rendered (does not run on very first render)
  - `ComponentWillUnmount()`
    - Runs when a component is removed from the DOM tree
    - Often used for doing cleanup
- Newer and more uncommon lifecycle methods
  - `shouldComponentUpdate()`
    - Lets React know if a component is affected by state/prop changes
    - Useful for when you don't want to render state/prop changes
    - Cannot update component state in this method
  - `getDerivedStateFromProps()`
    - Safer alternative to `componentWillReceiveProps()`
    - Called just before each render
    - Static function, so no access to `this`
    - Returns object to update state in response to prop changes
  - `getSnapshotBeforeUpdate()`
    - Safer alternative to `componentWillUpdate()`
    - Called right before DOM is updated
    - Return value is passed to `componentDidUpdate()`

### Hooks

Hooks are a feature from React 16.8 that allow the use of state, lifecycle methods, and other features in functional components. Without hooks, class components are required to use these.

#### Why Use Hooks?

- [Reusing stateful logic between components is hard](https://reactjs.org/docs/hooks-intro.html#its-hard-to-reuse-stateful-logic-between-components)
- [Complex components can become hard to understand](https://reactjs.org/docs/hooks-intro.html#complex-components-become-hard-to-understand)

## Links

- [Official React Website](https://reactjs.org/)
- [React Documentation](https://reactjs.org/docs/getting-started.html)
- [Components and Props](https://reactjs.org/docs/components-and-props.html)
- [StackOverflow - When to use ES6 class based React components vs. functional ES6 React components](https://stackoverflow.com/questions/36097965/when-to-use-es6-class-based-react-components-vs-functional-es6-react-components)
- [The Odin Project - Lifecycle Methods](https://www.theodinproject.com/courses/javascript/lessons/lifecycle-methods)
- [Programming with Mosh - React Lifecycle Methods - A Deep Dive](https://programmingwithmosh.com/javascript/react-lifecycle-methods/)
- [React Lifecycle Methods Diagram](https://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/)
- [React Router Quick Start](https://reactrouter.com/web/guides/quick-start)
