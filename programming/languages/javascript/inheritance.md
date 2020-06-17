# Prototypal Inheritance in JavaScript

## Basics

- When you want to implement inheritance, you attach properties and methods to the prototype
- Every JS function has a **prototype property**
    - The prototype property is empty by default
    - The prototype property is not enumerable
- Every JS object has a **prototype attribute**
    - Points to the object's parent
    - Set automatically when the object is created
- All JS objects inherit the following properties and methods from `Object.prototype`:
    - `constructor`
    - `hasOwnProperty()`
    - `isPrototypeOf()`
    - `propertyIsEnumerable()`
    - `toLocaleString()`
    - `toString()`
    - `valueOf()`

## Constructors

- Functions used for initializing new objects
- Called using the `new` keyword
- All objects inherit a `constructor` property that points to the constructor of the object
- If an object is created with an object literal, it inherits from Object.prototype; if an object is created from a constructor, it inherits from the constructor

## Prototypes

- Every object's prototype is either `null` or references another object
- The `prototype` property is internal and hidden, though there's a few ways to access it
    - You can use `myObject.__proto__`
        - This is a historical getter/setter
        - Has been replaced with `Object.getPrototypeOf` and `Object.setPrototypeOf`
- Prototypes are only used for reading
    - All write/delete operations operate directly on the object
    - Accessor functions are an exception, since calling a setter is technically writing
- The `this` keyword is not affected by prototypes
- Currently, the recommended way of setting the prototype of an object is [`Object.create`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/create)

## Links

- [JavaScript is Sexy - Javascript Prototype in Plain Language](https://javascriptissexy.com/javascript-prototype-in-plain-detailed-language/)
- [JavaScript.info - Prototypical Inheritance](https://javascript.info/prototype-inheritance)
- [The Odin Project - Objects and Object Constructors](https://www.theodinproject.com/courses/javascript/lessons/objects-and-object-constructors)
