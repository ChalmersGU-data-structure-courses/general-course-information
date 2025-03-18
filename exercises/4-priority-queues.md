# Exercises: Priority queues

**Note:**
The exercises are optional, but highly recommended.
If you are uncertain about any problem or want to discuss, write in the course discussion channel, or ask a teacher.

The exercises are divided into ***core*** and ***bonus***.
We recommend you try all the core exercises.
Try some of the bonus exercises if you want to learn more.

## Core exercises

**A1**.
Insert the following elements in sequence into an empty min-heap: 6, 8, 4, 7, 2, 3, 9, 1, 5.
Draw both the tree and array representations of the heap.
Now repeatedly delete the minimum element until the heap is empty.

**A2**.
Describe how to use a priority queue to implement: a) a queue, b) a stack.
Why can a priority queue not be used to implement a double-ended queue?

**A3**.
Write in pseudocode an algorithm for checking that a binary tree satisfies the heap property.
Now write the same algorithm but for a heap represented as an array.

<details markdown=block style="margin-bottom: 16px"><summary markdown=span>*Hint:*</summary>
Be careful to handle the case where a node has only a left child!
</details>

**A4**.
Design an algorithm that takes an array of numbers, and prints out the largest k numbers in the array, in ascending order.
For example, if k=4 and the array is {3, 1, 4, 1, 5, 9, 2, 6}, the program should print 4, 5, 6, 9.
The program should take O(n log(k)) time, where n is the length of the array.
It is not allowed to modify the array, and the amount of extra memory it uses should be proportional to k.

**A5**.
In the lecture we saw an algorithm for sorting a list using a priority queue.
Suppose we execute this algorithm, but implement the priority queue using an unsorted array.
This is equivalent to one of the sorting algorithms we saw in week 1.
Which one?
Now, answer the same question, but where the priority queue is implemented using a sorted array.

## Bonus exercises

**B1**.
Design a data structure that supports the following operations:

- `add(x: Item)`: add an item to the collection.
  (Duplicates are allowed.)
- `median() -> Item`: return the *median* (the item which would sit in the middle if the collection was sorted).
- `removeMedian() -> Item`: remove the median.

Finding the median should take O(1) time, and the other two operations should take O(log(n)) time.

<details markdown=block style="margin-bottom: 16px"><summary markdown=span>*Hint:*</summary>
Use two priority queues.
</details>

**B2**.
Show how to define a priority queue where `max` takes constant time and `add` and `removeMax` take logarithmic time, *with the help of a red-black BST.*

<details markdown=block style="margin-bottom: 16px"><summary markdown=span>*Hint:*</summary>
Use the BST to store the priority queue but also remember the maximum value.
</details>

**B3**.
Suppose you want a data structure with only the operations `insert` and `getMin`.
What is the most efficient way to implement it?

**B4**.
(Very optional bonus question)
Read up on [treaps](http://jeffe.cs.illinois.edu/teaching/algorithms/notes/03-treaps.pdf), which use ideas from heaps to build a balanced BST.
Implement them in your favourite programming language!
