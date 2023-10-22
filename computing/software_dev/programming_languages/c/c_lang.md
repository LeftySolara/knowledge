# The C Programming Language (WIP)

***Note***: *These notes are a work-in-progress and still need to be processed, re-organized, and cleaned up. Currently the information here is just a simple brain dump of everything I've read and learned recently. Over time I will go through these and make them more concise and understandable. These notes were written using [[Using Obsidian|Obsidian]] with a lot of plugins, and the formatting displayed by those plugins may not appear correctly on the hosted version of these notes (where you're reading them now). These formatting issues will also be fixed when I go though and process these notes.*

C is a general-purpose, procedural programming language developed by Dennis Ritchie at Bell Labs between 1972 and 1973. It is one of the most widely-used languages and was standardized by ANSI in 1989. This document will mainly refer to C17, as most of the source documentation does. See [[#References]] for a list of sources.

## The Basics

In this section we will cover a bit about programming in general.

### Imperative Programming

- C programs have the computer do specific tasks by giving orders
- The orders are similar to how humans would express things in the imperative tense in spoken languages
    - So, the term *imperative programming* was coined for this way of organizing computer programs

> [!tip] Takeaway
> C is an imperative programming language.

- The code displayed below will be our example for explaining various aspects of C. The end result of it is outputting 5 lines of text on the console.

#### Code Sample: print_squares.c

```c title:print_squares.c
/* Include the needed libraries. */
#include <stddef.h>
#include <stdio.h>
#include <stdlib.h>

/* The main thing that the program does. */
int main(void)
{
    /* Declarations */
    double arr[5] = {
        [0] = 3.0,
        [1] = 7.3,
        [3] = .06007,
        [4] = 3.E+21,
    };

    /* Doing some work. */
    for (size_t i = 0; i < 5; ++i) {
        printf("element %zu is %g, \tits square is %g\n", i, arr[i], arr[i] * arr[i]);
    }

    return EXIT_SUCCESS;
}
```

- And here is the output of the program in the console:

```ln:false file:"Output from print_squares.c"
element 0 is 9,         its square is 81
element 1 is 2.9,       its square is 8.41
element 2 is 0,         its square is 0
element 3 is 7e-05,     its square is 4.9e-09
element 4 is 3e+25,     its square is 9e+50
```

We will reference this code frequently throughout the beginning of this article. For now, just remember that it orders the computer to print text to the console.

### Compiling and Running

The code in [[#Code Sample print_squares.c|print_squares.c]] is just another piece of text that exists on your hard drive. To actually run, it needs to be translated into a form that can be understood by your computer. A special program called a *compiler* does this for us. It translates the C code into *binary code* (also called an *executable)*), which your computer can read and understand. This process is called *compiling*.

> [!tip] Takeaway
> C is a compiled programming language.

Which compiler you use will depend on the *platform* on which you will be running your program. This is because the binary code is *platform dependent*. Basically, different types of machines speak different languages. Your computer understands a different binary format than your phone or your camera. One of the main reasons C exists is that it provides a level of abstraction for all the different machine-specific languages. This abstraction is usually called an *assembler*.

> [!tip] Takeaway
> A correct C program is portable between different platforms.

Some platforms claim to be "C" but do not conform to the latest standards. There are also platforms that accept "incorrect" programs or provide extensions to the C standard that are not widely portable. Because of this, running and testing a program on a single platform will not always guarantee portability. By *portable*, we mean that whenever you run the program, its behavior should be the same.

It's the compiler's job to ensure that your program will run correctly on various platforms after being translated.

The process of compiling your program will differ based on your compiler. Here we will use `gcc` for our examples. You may want to check which compiler your system uses and look up the documentation for it.

An example of compiling a C program using gcc:

```bash ln:false
gcc print_squares.c -o print_squares
```

Here the compiler takes the file `print_squares.c`, translates it into binary code, and outputs that binary code to a file called `print_squares`.

When compiling programs, you may get warnings from the compiler. If that happens, pay attention to what they're saying and attempt to fix them as best you can. The compiler is there to help you, and therefore you should listen to it when it has something to say.

> [!tip] Takeaway
> A C program should compile cleanly without warnings.

Note that while the above statement is a good goal to have, it is not always possible. There are many widely-used C programs that ship with compiler warnings. A better way to phrase this statement is that *a C program should compile with as few warnings as possible*.

### The Structure of A Program

#### Grammar

- A C program is composed of different types of text elements that are assembled together
- Special Words
    - Represent concepts and features in C that cannot be changed
    - Examples: `#include`, `int`, `void`, etc.
- Punctuation
    - C uses several types of punctuation to structure program text
    - Five different kinds of brackets: {}, (), [], /* \*/, <>
        - Used to group certain parts of the program together
        - Should always come in pairs
    - Two different separators or terminators: comma and semicolon
        - Commas separate things
        - Semicolons terminate things
    - Comments
        - Denoted by // and /* \*/
        - Ignored by the compiler
        - Perfect place to explain and document code
    - Literals
        - Fixed values that are a part of the program
    - Identifiers
        - Names given to different entities in a program
        - They may refer to:
            - Data objects / variables
            - Type aliases
            - Functions
            - Constants
    - Functions
    - Operators
    
#### Declarations

- Before we can use an identifier, it must be declared
- Declaring specifies what the identifier is supposed to represent
- Different from keywords; keywords are predefined by the language and must not be declared or redefined

> [!tip] Takeaway
> All identifiers in a program have to be declared.

- Some examples of identifiers in [[#Code Sample print_squares.c|print_squares.c]] are `arr` and `i`
- Variables are named items that allow us to store values
- Declarations are bound to the scope in which they appear.

#### Definitions

- Identifiers only specify the kind of object it refers to, not what it is
- *Definitions* are what identifiers identify

> [!tip] Takeaway
> Declarations specify identifiers, while definitions specify objects.

- *Initialization* is an augmented declaration where an initial value is provided. For example: `size_t i = 0`

> [!tip] Takeaway
> An object is defined at the same time it is initialized.

- Each object or function must have exactly one definition

#### Statements

- *Statements* are instructions that tell the compiler what to do with identifiers

## An Introduction to C

This section will provide information for writing good, modern C programs. By "good", we mean modern and portable.

### Control Flow

- C has five conditional *control statements*: `if`, `for`, `do`, `while`, and `switch`
    - `if` introduces a conditional execution depending on a Boolean expression
    - `for`, `do`, and `while` are different forms of iterations
    - `switch` is a multiple selection based on an integer value

#### Conditional Execution (`if` statements)

An *`if` statement* looks something like this:

```c title:if.c
if (i > 25) {
    j = i - 25;
}
```

In this example we compare `i` to the value 25. If it is larger than 25, then the value of `j` is set to `i - 25`. The expression `i > 25` is called the *controlling expression* and the part in `{ ... }` is called the *dependent block* or *dependent statement*.

Note that there is only one part inside the parentheses, which determined whether the dependent statement or block is run once or not at all. This is different from a `for` loop, which we will discuss later.

Another, more general form of the `if` statement is as follows:

```c title:if_else.c
if (i > 25) {
    j = i - 25;
}
else {
    j = i;
}
```

This has a second dependent statement or block that is executed if the controlling condition is not fulfilled. This is done by adding the keyword `else` that separates the two statements or blocks.

The `if (...) ... else ...` is called a *selection statement*. It selects one of the two *code paths* according to the contents of `( ... )`. The general form of this is

```c title:selection_statement.c ln:false
if (condition) {
    statement0-or-block0
}
else {
    statement1-or-block1
}
```

Here, `condition` can be a number of things ranging from simple to very complex nested expressions. The simplest example can be seen below.

```c title:simple_if.c
for (size_t i = 0; i < 5; ++i) {
    if (i) {
        printf("%d\n", i);
    }
}
```

In this example, the condition that determines whether `printf` runs is just `i`. A numerical value by itself can be interpreted as a condition. The text will only be printed when the value of `i` is not 0.

There are two simple rules for the evaluation of a numerical condition:
- The value `0` represents logical false.
- Any value different from `0` represents logical true.

The operators ` == ` and `!=` allow for testing equality and inequality. `a == b` is true if the value of `a` is equal to the value of `b`; `a != b` is false if `a` is equal to `b`, and true otherwise.

### Iterations

#### `for` Loops

In the example `sample_if.c` we encountered the `for` statement. The general form of this statement is

```c title:for.c ln:false
for (clause1; condition2; expression3) {
    statement-or-block
}
```

Usually, `clause1` is an assignment expression or variable definition. It sets the initial value for the iteration domain. `condition2` tests whether the iteration should continue. Then, `expression3` updates the iteration value used in `clause1`. It is performed at the end of each iteration.

Here is an example:

```c title:for2.c ln:false
for (size_t i = 0; i < 5; ++i) {
    do_something(i);
}
```

In this example, the `for` counts up from 0 to 5, exclusive. When the value of `i` is greater than or equal to 5, the loop stops.

Note that the iteration variable is named `i`. It is common to use the letters "i" and "j" as names for this variable.

> [!tip] Takeaway
> It is customary to use the name `i` for your iteration variable. A loop nested inside the initial loop will use the name `j`, the loop nested inside that will use `k`, and so on. Note this this is only done when using "throwaway" variables.

#### `while` Loops

The two other iterative statements in C are `while` and `do`. Their basic forms are:

```c title:"while loop" ln:false
while (condition) {
    statement-or-block;
}
```

```c title:"do-while loop" ln:false
do {
    statement-or-block;
} while (condition);
```

Here is an example of a normal `while` loop:

```c title:while.c ln:false
size_t i = 10;
while (i > 3) {
    do_something();
}
```

In this example, `do_something` will execute repeatedly until the value of `i` is less than or equal to `3`.

The `do-while` loop is very similar, except that it checks the condition *after* the dependent block:

```c title:do-while.c ln:false
size_t i = 10;
size_t j = 20;
do {
    i = j + 1;
} while (i < j);
```

This means that if the condition evaluates to `false`, the `while` loop will not run at all while the `do` loop will run one before terminating. Basically, if you want to run a `while` loop that always executes at least once, this is the way to do it.

#### `break` And `continue`

All three iteration statements become even more flexible with `break` and `continue` statements. A `break` statement stops the loop immediately:

```c title:break.c ln:false
while (true) {
    double prod = a * x;
    if (fabs(1.0 - prod) < eps) {
        break;
    }
    x *= (2.0 - prod);
}
```

Here, once the loop executes the `break` statement, it immediately terminates. The same can be done for `for` loops.

The `continue` statement is similar to `break` in that it skips the iteration of the rest of the dependent block. However, instead of terminating the loop, it instead re-evaluates the condition and continues from the start of the dependent block if the condition is true. Basically, it skips the rest of the current iteration of the loop and moves to the next iteration.

### Multiple Selection

The final control statement in C is the `switch` statement. It is a *selection* statement and is mainly used when cascades of `if-else` blocks would be too tedious:

```c title:tedious_if.c ln:false
if (arg == 'm') {
    puts("magpie");
}
else if (arg == 'r') {
    puts("raven");
}
else if (arg == 'j') {
    puts("jay");
}
else if (arg == 'c') {
    puts("chough");
}
else (
    puts("unknown");
)
```

In this case, we have a choice that is more complex than a `false-true` decision and that can have several outcomes. We can simplify this by using a `switch` statement:

```c title:switch.c ln:false
switch (arg) {
    case 'm':
        puts("magpie");
        break;
    case 'r':
        puts("raven");
        break;
    case 'j':
        puts("jay");
        break;
    case 'c':
        puts("cough");
        break;
    default:
        puts("unknown");
}
```

Here, we select one of the `puts` calls according to the value of `arg`. We provide specific cases for the characters `m`, `r`, `j`, and `c` and a fallback case labeled `default`. The default case is triggered if `arg` doesn't match any of the `case` values.

Syntactically, a `switch` is as simple as

```c title:switch_syntax.c ln:false
switch (expression) {
    statement-or-block
}
```

and its semantics are straightforward: `case` and `default` serve as *jump targets*, which means that the program's execution will jump to them when a certain condition is met. If we hit a `break` statement, the whole `switch` terminates.

There are two things to note about `switch` statements:
- `case` values must be integer constant expressions
- `case` labels must not jump beyond a variable definition

## References

### Websites

- [cppreference](https://en.cppreference.com/w/c)

### Books

- [The C Programming Language, 2nd Edition](https://www.amazon.com/Programming-Language-2nd-Brian-Kernighan/dp/0131103628)
- [Jens Gustedt - Modern C](https://www.manning.com/books/modern-c)
- [Ben Klemens - 21st Century C](https://www.oreilly.com/library/view/21st-century-c/9781491904428/)

### Articles

- [Object-oriented Design Patterns in the Linux Kernel](https://lwn.net/Articles/444910/)
- [Malloc Tutorial](https://danluu.com/malloc-tutorial/)
- [X-Macros](https://en.wikipedia.org/wiki/X_Macro)
