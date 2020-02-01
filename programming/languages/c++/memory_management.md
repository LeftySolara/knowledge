# Memory Management in C++

## Allocating Memory

The C++ way of allocating memory is by using the `new` operator. `new` will allocate memory, initialize it, and return its address (which can be assigned to a pointer).

Examples of using the `new` operator to initialize a pointer:

```
int *a = new int;       // Just allocate memory
int *b = new int(12);   // Allocate and initialize memory
```

The operator can also be used to allocate blocks of memory:

```
int *numbers = new int[15];  // Allocate memory for an array with 15 elements
```

When allocating blocks of memory, the `new` operator returns a pointer to the first element.

If there is not enough heap memory available, then `new` throws an exception of type `std::bad_alloc`. If `nothrow` is used, then it returns a NULL porinter instead.

## Deallocating Memory

To deallocate memory, use the `delete` operator:

```
int *a = new int(12);
delete a;
```

For blocks/arrays allocated using `new`, use the following form for `delete`:

```
int *numbers = new int[15];
delete[] numbers;
```

## A Word on `malloc`

In C++ is it considered best practice to use `malloc` as little as possible. Instead, programmers should make use of the `new` and `delete` operators. There are a few reasons for this:
- `malloc` is not type-safe, while `new` and `delete` are
- `malloc` only allocates chunks of raw memory, while `new` calls class constructors

There are situations where it makes sense to use `malloc`, such as when you need a `realloc`-like operation performed. It should also be noted that you cannot mix `malloc`/`free` and `new`/`delete`.

## Allocators

An **allocator** is an object used to encapsulate memory management. Allocators are useful when you want to separate allocation and construction. It is also useful for separating deallocation and destruction.

By default, all STL containers use `std::allocator`. This uses the `new` and `delete` operators to allocate and free memory from the heap.

A example of an allocator declaration:

```
template <class T>
class allocator;
```

One use case for allocators is control over construction. The `new` operator does not allow you to control which constructors are called, but an allocator can.

For more information, see [this article](https://www.geeksforgeeks.org/stdallocator-in-cpp-with-examples/).

## Links

[GeeksforGeeks - new and delete operators in C++](https://www.geeksforgeeks.org/new-and-delete-operators-in-cpp-for-dynamic-memory/)
[GeeksforGeeks - std::allocator in C++](https://www.geeksforgeeks.org/stdallocator-in-cpp-with-examples/)
[StackOverflow - In what cases do I use malloc and/or new?](https://stackoverflow.com/questions/184537/in-what-cases-do-i-use-malloc-and-or-new)
