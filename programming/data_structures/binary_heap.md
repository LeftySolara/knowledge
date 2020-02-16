# Binary Heap

A **binary heap** is a complete binary tree that satisfies the heap property. The **heap property** is defined as follows:

1) In a *max heap*, the value of each node is less than or equal to the value of its parent

2) In a *min heap*, the value of each node is greater than or equal to the value of its parent.

In a max heap, the maximum element is stored at the root. In a min heap, the minimum element is stored at the root.

## Array Implementation

Because binary heaps are complete trees, they can be represented using an array containing their level-order traversal. Take the following heap:

```
          A
       /     \                      
      D       F               This heap would be represented by the array
    /  \    /  \                          [A,D,F,B,C,G,E,H]
   B    C  G    E
  /
H
```

In the array implementation, the following are true for the *k*-th element:
- Its left child is located at the index `2k`
- Its right child is located at the index `2k+1`
- Its parent is located at the index `k/2`

When using the array implementation the first item in the array is usually left empty, with the root being at `arr[1].` The is done to make the previously described arithmetic work out.

## Insertion

Inserting an item into a binary heap works as follows:
1) Appended the new item to the end of the array.

2) Repair the heap ordering.

To repair the ordering and restore the heap property after adding an item, take the following steps:
1) Compare the newly added item with its parent.

2) Swap the positions of the new item and its parent.

3) For a min heap, continue this process until the value of the parent is greater than or equal to the value of the new item. For a max heap, continue until the parent is less than or equal to the new item.

## Deletion

The minimum (for a min heap) or maximum (for a max heap) value of a heap can always be found at the root. To remove it from the heap:
1) Remove the root node from the heap.

2) Replace the root node with the last node in the heap.

3) Restore the heap property by percolating down (similar to what's done for insertion, but in reverse).

## Links

- [Carnegie Mellon University - Binary Heaps](https://www.cs.cmu.edu/~adamchik/15-121/lectures/Binary%20Heaps/heaps.html)
- [Geeksforgeeks - Binary Heap](https://www.geeksforgeeks.org/binary-heap/)
- [Wikipedia - Heap (data structure)](https://en.wikipedia.org/wiki/Heap_(data_structure))
