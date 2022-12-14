# codecademy_heap_and_heapsort

Introduction to heaps

Heaps are used to maintain a maximum or minimum value in a dataset.

Imagine you have a demanding boss (hopefully this is theoretical!). They always want the most important thing done. Of course, once you finish the most important task, another one takes its place.

You can manage this problem using a priority queue to ensure you’re always working on the most pressing assignment and heaps are commonly used to create a priority queue.

Heaps that track the maximum value in a dataset are max-heaps while heaps that track the minimum value are referred to as min-heaps. We will focus on max-heaps in this article, but the concepts for a min-heap are nearly identical.

Think of the max-heap as a binary tree with two qualities:

The root is the maximum value of the dataset.
Every parent’s value is greater than its children.
These two properties are the defining characteristics of the max-heap. By maintaining these two properties, we can efficiently retrieve and update the maximum value.

Heap representations

We can picture max-heaps as binary trees, where each node has at most two children. As we add elements to the heap, they’re added from left to right until we’ve filled the entire level.

<img width="550" alt="image" src="https://user-images.githubusercontent.com/82447615/188422853-953b0104-10fb-43b0-b7d1-f074432d2bee.png">


max-heap diagram

Note: The examples in this article use numbers since this is a straightforward value, but heaps have many practical applications.

At the top, we have our root value, 11. Then, we’ve filled the next level containing the root value’s children, 10 and 9. The next addition will be added as the left child of 10, starting a new level in the tree. We would continue filling this level from left to right until 9 had its right child filled.

Conceptually, the tree representation is beneficial for understanding. Practically, we implement heaps in a sequential data structure like an array or list for efficiency.

Notice how by filling the tree from left to right; we’re leaving no gaps in the array. The location of each child or parent derives from a formula using the index.

left child: (index * 2) + 1
right child: (index * 2) + 2
parent: (index - 1) / 2 — not used on the root!
Adding an element

Sometimes you will add an element to the heap that violates the heap’s essential properties.

We’re adding 18 as a left child of 2, which violates the max-heap property that parents must be larger or equal to their child.

We need to restore the fundamental heap properties. This restoration is known as heapify or heapifying. We’re adding an element to the bottom of the tree and moving upwards, so we’re heapifying up.

As long as we’ve violated the heap properties, we’ll swap the offending child with its parent until we restore the properties, or until there’s no parent left. If there is no parent left, that element becomes the new root of the tree.

18 swaps with 2, but there’s still work to do because now 18 is a child of 11. One more swap and we’ve restored the heap properties. The child value, 18, is lesser than the parent and root of the tree, 20. We can see that 18‘s children 11 and 10 are also smaller than their parent.

Heapify Up Demonstration
<img width="547" alt="image" src="https://user-images.githubusercontent.com/82447615/188423212-2e55d7e3-5c54-4c41-9308-82d82a8b92ce.png">


Review

Nice job reaching the end of this article! Let’s review what we learned:

A max-heap tracks the maximum element as the element within a data set.
Max-heaps must maintain the heap property that the parent values must be greater than their children.
When adding elements, we use .heapify_up() to compare the new element with its parent; if it violates the heap property, then we must swap the two values.
