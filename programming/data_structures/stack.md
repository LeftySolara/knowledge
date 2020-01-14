# Stack

A **stack** is an ordered, linear structure whose items are added and removed at the same end. This end is usually called the "top" of the stack.

Because items are added and removed from the same end, any removal operation will always affect the most recent item placed on the stack. This type of pattern is called **last-in first-out (LIFO)**.

A real-world example of this is stacking plates in the kitchen. Let's say you have a collection of different colored plates. If you stack one plate on top of another and stack another on top of that, you will have a stack with three plates. In order to get to the lower plates, you would have to remove the plates above them first. Adding a plate to the top of the stack is equivalent to the `push` operation and removing a plate from the top is equivalent to `pop`.

Here is an example of what a stack of colored plates looks like:

```
blue     <--- top
orange
yellow
red
purple   <--- base
```

In this example, the purple plate is a the bottom of the stack because it was added first. This position is ususlly called the **base**. The blue plate is at the top of the stack, as it was added most recently.

Stacks are useful for reversing the order of items. Because of the way items are added and removed, it follows that the order of insertion is the reverse of the order of removal.

## Basic Stack Operations

Most stack implementations have the following operations:

- `push(item)`: adds an item to the top of the stack
- `pop()`: removes an item from the top of the stack and returns it
- `peek()`: returns the top item from the stack, but does not remove it