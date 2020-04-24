# JavaScript Basics

## Data Types

JavaScript is a dynamically-typed language. Here are descriptions of the various data types available.

### Number

JavaScript only has one number type, which represents integers and floating point numbers. They can also be written in scientific notation, hex notation, and octal.

```
var a = 1;       // Plain, whole number
var b = 1.2;     // Number with a decimal
var c = 123e5;   // 12300000
var d = 123e-5;  // 0.00123
var e = 0xFF;    // 255
var f = 0377;    // 255
```

The `Number` type cannot represent values larger than `2<sup>53</sup>` or less than `-2<sup>53</sup>` because of its internal representation.

#### Precision

Integers are accurate up to 15 digits:

```
var a = 999999999999999;     // will be 999999999999999
var b = 9999999999999999;    // will be 10000000000000000
```

The maximum number of decimal places is 17. Floating point arithmetic is not always 100% accurate (as with most languages).


#### Adding Numbers and Strings

JavaScript uses the `+` operator for addition and concatenation.

- Adding two numbers results in a number
- Adding two strings results in string concatenation
- Adding a number and a string results in string concatenation

Note that strings will be converted to numbers in numberic operations.


#### NaN

`NaN` is a keyword representing a computational error. Doing any kind of arithmetic with a non-numeric string will result in `NaN`.

`NaN` is sticky, meaning any operation on `NaN` returns `NaN`.

You can use `isNaN()` to find out if a value is a number.


#### Infinity

`Infinity` represents the mathematical infinity. If you calculate a number that's larger than the largest possible JS number, the result is `Infinity`. Dividing by 0 also returns `Infinity`.

`-Infinity` can also be referenced.


#### Numbers as Objects

Normally numbers are primatives, but they can be defined as objects by using the `new` keyword:

```
var x = new Number(999);
```

This is usually a bad idea as it can increase execution time and complicates the code. For example:

```
var a = 500;
var b = new Number(500);
var c = new Number(500);

// (a == b) is true because the values are equal
// (a === b) is false because the types are different
// (b == c) is false because objects cannot be compared
```

### BigInt

`BigInt` was recently added to represent integers of arbitrary length. They can be created by appending `n` to the end of an integer literal.

As of this writing, only Firefox and Chrome support `BigInt`. To read more about this type, try [this article](https://javascript.info/bigint).


### String

A string in JavaScript must be surrounded by quotes. You may use single quotes, double quotes, and backticks.

Strings in single and double quotes are "simple" and there is almost no difference between them.

Backticks are "extended functionality" quotes and let us embed expressions by wrapping them in `${...}` (similar to Bash).

There is no "character" type in JavaScript.


### Boolean

Booleans have two values: `true` and `false`.


### Null

The `null` type contains only the `null` value. It is a special value that represents "nothing", "empty", or "value unknown". It is *not* a reference to a non-existing object or a null pointer.


### Undefined

Like `null`, `undefined` is its own type. It represents "value is not assigned". If a variable is declared but not assigned, then its value is `undefined`.

You can assign `undefined` to a variable, but it's not recommended. Use `null` instead.


## Arithmetic

The arithmetic operators in JavaScript are:

`+` addition
`-` subtraction
`*` multiplication
`**` exponentiation
`/` division
`%` modulus
`++` increment
`--` decrement

These operators can work on literals, variables, or expressions.


## Links
- [Data Types in JavaScript](https://javascript.info/types)
- [JavaScript Numbers](https://www.w3schools.com/js/js_numbers.asp)
- [JavaScript Arithmetic](https://www.w3schools.com/js/js_arithmetic.asp)
- [JaveSctipt Operator Precedence](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence#Table)
