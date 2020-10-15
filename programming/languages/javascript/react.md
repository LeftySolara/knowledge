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

## Links
* [Official React Website](https://reactjs.org/)
* [React Documentation](https://reactjs.org/docs/getting-started.html)
* [Components and Props](https://reactjs.org/docs/components-and-props.html)
* [StackOverflow - When to use ES6 class based React components vs. functional ES6 React components](https://stackoverflow.com/questions/36097965/when-to-use-es6-class-based-react-components-vs-functional-es6-react-components)
