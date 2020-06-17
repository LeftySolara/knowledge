# Dynamic Array

A **dynamic array** is an array that has automatic resizing.

## Pros
- Fast lookups
- Variable size
- Cache-friendly (because items are stored in contiguous memory)

## Cons
- Worst-case for appends is slow (because underlying array needs to expand)
- Inserts and deletes are costly (because items need to be shifted around)

## Implementation

Dynamic arrays are usually implemented by encapsulating and manipulating a normal, underlying array. The **size** of the dynamic array is the number of items being held, and its **capacity** is the total number of items it can hold without needing to expand (which is equal to the length of the underlying array).

### Appending

To add an item to a dynamic array when its underlying array is full, the underlying array will need to be expanded. In this case, the array cannot be expanded directly since other programs might be using that memory. Instead a new, larger array is created and the items are copied to the new array. The new array is usually double the size of the original.

### Deleting

Removing items from dynamic arrays works just like removing from regular arrays, except items need to be shifted over to keep them contiguous in memory. 

## Links
[Interview Cake - Dynamic Arrays](https://www.interviewcake.com/concept/java/dynamic-array)
