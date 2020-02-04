# Iterators in C++

**Iterators** are pointer-like objects used to navigate, retrieve items from, and manipulate containers. They can be incremented with `++`, decremented with `--`, and compared with `!=`. There are many different types of iterators which all behave differently.

Iterators are useful becuase they are more generic than regular pointers.

## Types of Iterators

Iterators can be separated into a number of different categories. Each category describes the types of operations an iterator can perform, and more powerul iterators are often derived from weaker ones.

### Input Iterators

This is the most simple form of iterator. All STL containers return at least this level. They are only used to read from containers.

Input iterators can use `++iter` or `iter++` to increment, `*iter` to dereference, and `!=`/`==` to compare to other iterators.

Examples of input iterators are the `begin` and `end` iterators provided by most STL containers.

### Output Iterators

Output iterators are basically the opposite of input operators. They are only used for storing data in a container. They cannot be used for reading data and have no comparison operators.

These iterators use `++iter` and  `iter++` to increment, and `*iter=` for assignment.

### Insert Iterators

Insert iterators are a type of output iterator. They allow for "pointing" to a place in a container and inserting items in that location.

Insertions are performed with `*iter = value`. This type of iterator does not need to be incremented; you can just keep inserting.

These iterators are created with one of the following:

- `back_inserter<container>`
    - returns an output iterator pointing to the end of the container
    - output to this iterator is added to the end of the container
- `front_inserter<container>`
    - returns an output iterator pointing to the front of the container
    - output to this iterator is added to the front of the container
- `inserter<container, iterator>`
    - returns an output iterator pointing to the location pointed to by `iterator`
    - output to this iterator is added to the container at this location from that point forward

### Ostream Iterators

Ostream iterators allow you to insert into an output stream. This basically means writing to the output stream.

### Istream Iterators

Istream iterators are a type of input iterator. They let you read from an input stream.

## Links
[Northwestern University - C++ Iterators](https://users.cs.northwestern.edu/~riesbeck/programming/c++/stl-iterators.html)
[Geeksforgeeks - Introduction to Iterators in C++](https://www.geeksforgeeks.org/introduction-iterators-c/)
