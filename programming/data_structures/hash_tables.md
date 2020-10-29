# Hash Tables

A **hash table** is a data structure used to store data in key-value pairs. The table itself is usually implemented as an array.

Hash tables are often useful for searching in _O(1)_ time with high probability.

## Common Uses

- Implementation of associative arrays
- Database indexing
- Spell checking
- Compilers and interpreter environments
- Network routing
- Substring searching
- File and directory synchronization
- Cryptography
- Caching
- Object representation in OOP languages

## Basics

The simple approach to implementing a hash table is creating a large array to hold all available data, indexed by keys. This is called a **direct access table**.

There are two major problems with this approach:

1. It assumes that keys are always integers, which is often not the case.
2. It is not memory-efficient.

The first issue can be addressed by _prehashing_, while the second is handled by _hashing_.

## Prehashing

**Prehashing** is the process of mapping keys to non-negative integers. This allows us to uniquely identify an object from a group of similar objects. For example, an employee might be assigned a unique ID number that is used to look up certain information about them.

In theory keys would be finite and descrete, where `h(x) = h(y) <=> x = y` (where h is some function and x and y are arbitrary keys). This is usually not the case.

## Hashing

**Hashing** is the process of reducing a universe `U` of all keys down to a reasonable size `m`. This is done using a _hash function_.

A **hash function** is any function that maps a data set of arbitrary size (our universe `U`) to a data set of fixed size (that array size `m`). This allows us to store an arbitrary amount of information into a hash table's fixed-size array.

Good hash functions often have the following properties:

- Easy to compute
- Prioritize uniform distribution
- Minimize the possible number of collisions

Hashing generally works as follows:

```
hash  = prehashFunction(key)    // prehashing
index = hash % array_size       // hashing
```

Ideally `m` would be close to `n`, where `n` is the number of keys in the hash table. That way the space used is proportional to the table size and less memory is wasted.

### Common Hash Function Methods

#### Division Method

One of the most common types of hash functions uses simple division to generate an index:

```
h(k) = k mod m
```

where `k` is the value obtained from the prehash and `m` is the size of the hash table array.

#### Multiplication Method

Here we multiply some pseudo-random integers and do some bit shifting:

```
h(k) = [(a*k) mod 2^w] >> (w-r)
```

where `w` is the word size of the computer, `m = 2^r`, and `a` is some odd number that is not close to a power of 2.

#### Universal Hashing

This method is very effective due to the amount of randomness generated:

```
h(k) = [(ak+b) mod p] mod m
```

where `a`, `k`, and `b` are random numbers between 0 and `p-1`, and `p` is some prime number > `U`.

## Collision Resolution

A **collision** occurs when two or more keys have the same hash, and thus need to be stored in the same place in the table. Collisions are very likely, so maintaining performance of a hash table is heavily dependent on how they are handled.

There are various methods used for handling collisions.

### Chaining (Open Hashing)

Chaining is a commonly-used technique for dealing with collisions.

Here, each index of the hash table's array is filled with a linked list. The actual data being stored is then inserted into the list at whatever index results from hashing. If an element needs to be stored in an occupied slot of the table, it is added to the end of the respective linked list.

The expected length of a chain for `n` keys and `m` slots is `n/m`. This is called the **load factor**. This value is used to determine when to increase the size of the hash table's underlying array.

The worst case for chaining is the situation in which all the data is stored in the same list. In this case, searching is _O(n)_. This usually doesn't happen because good hash functions try to achieve uniform distribution.

### Linear Probing (Open Addressing)

Linear probing is usually used when data is stored in the table array directly. If a value needs to be inserted into an occupied slot, we probe the array until an empty space is found. In this case, that means iterating over the array one slot at a time.

### Quadradic Probing

Quadradic probing is similar to linear probing, except the interval between probes is a polynomial instead of an integer.

### Double Hashing

Double hashing is similar to linear probing, except the interval between probes is defined by a second hash function.

## Links

- [What is a HashTable Data Structure - Introduction to Hash Tables , Part 0](https://www.youtube.com/watch?v=MfhjkfocRR0)
- [HackerEarth - Basics of Hash Tables](https://www.hackerearth.com/practice/data-structures/hash-tables/basics-of-hash-tables/tutorial/)
- [MIT 6.006 Introduction to Algorithms, Lecture 8: Hashing with Chaining](https://www.youtube.com/watch?v=0M_kIqhwbFo&list=PLUl4u3cNGP61Oq3tWYp6V_F-5jb5L2iHb&index=8)
