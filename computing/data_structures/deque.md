
# Deque

## What is it?

A **deque** (also called a **double-ended queue**) is an ordered collection of items similar to a [queue](queue.md). There is a front and a rear, and operations primarily take place on the ends.

Unlike queues, deques allow for insertion and removal from both ends. Because of this, there is no requirement for them to follow FIFO or LIFO ordering (though they can if you decide to do so). It can be thought of as a combination of a stack and queue. 

## Examples in Technology

Some use cases for deques include:
- Keeping track of web browser history
- Keeping track of undo operations
- Thread management

## Basic Deque Operations

- `addFront(item)`: Adds an item to the front of the deque
- `addRear(item)`: Adds an item to the rear of the deque
- `removeFront()`: Removes an item from the front of the deque
- `removeRear()`: Removes an item from the rear of the deque
