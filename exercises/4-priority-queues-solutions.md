# Exercise solutions: Priority queues

Here are suggested solutions to the exercises about priority queues.

## Core exercises

### A1. Insert into a min heap

Use the [binary heap visualisation tool](https://chalmersgu-data-structure-courses.github.io/dsvis/prioqueues.html?algorithm=BinaryHeap).

### A2. Implement X using a priority queue

**We can implement a queue** of items using a min-priority queue storing pairs (*item*, *k*) of an item and an integer *k*.
The priority queue compares according to the second component (the integer).
We maintain a counter *prio*, which starts from 0.
Adding an item to the queue is implemented by adding (*item*, *prio*) to the priority queue and incrementing *prio*.
Removing an item from the queue is implemented by removing the minimal pair (*item*, *k*) and returning the item.

(An analogy is a "nummerlappsmaskin" – when an item gets added, it takes a nummerlapp. Then, the items are removed in order of their nummer.)

**For a stack**: the same idea, but with a max-priority queue.
Alternatively, use a *decreasing* counter *prio*.

**We can't make a deque** this way, because with a min-priority queue we can only get the smallest item and with a max-priority queue we can only get the largest.
For a deque, we need to be able to get items at both ends, which is not possible to simulate using just a priority queue.
(However, you can make a deque using a [min-max heap](https://en.wikipedia.org/wiki/Min-max_heap).)

### A3. Checking the heap property

For a heap represented as a tree (choosing a recursive strategy):

```python
isHeap(node) -> bool:
    return isHeap(node, null)

isHeap(node, lowerBound) -> bool:
    return node == null or (
        (lowerBound == null or lowerBound ≤ node.key) and
        isHeap(node.left, node.key) and
        isHeap(node.right, node.key)
    )
```

For a heap represented as a **0-based** array (choosing, for example, an iterative strategy):

```python
isHeap(array):
    for i from 0 to array.size():
        for child in {2*i+1, 2*i+2}:
            if child < array.size() and not array[i] ≤ array[child]:
                return false
    return true
```

Note:
You can optimize the above code by stopping the loop at `array.size() / 2`.
(Why is that?)

### A4. Print *k* largest numbers

The idea is to use a *min-heap* containing the *k* largest numbers seen so far.
We read in each number one at a time, then we check it against the *k*<sup>th</sup>-largest number seen so far.
If the new number is bigger, we remove the *k*<sup>th</sup>-largest number from the min-heap and add the new number.

The reason to use a min-heap is that, if the heap contains the *k* largest numbers so far, then `getMin()` will return the *k*<sup>th</sup>-largest, and `removeMin()` will return it.

Here is an implementation in pseudocode:

```python
pq = new MinPriorityQueue()

# Read in numbers
for x in array:
    # A trick: we add the new number, then if the heap contains k+1 items we remove the smallest.
    # This has the same effect as the algorithm described above!
    pq.add(x)
    if pq.size() > k:
        pq.removeMin()

# Remove items in order of size
while not pq.isEmpty():
    print(pq.removeMin())
```

### A5. Sorting using a priority queue

An unsorted array gives you **selection sort** (add() just adds to the end of the array, but removeMin() has to do a linear search).

A sorted array gives you **insertion sort** (add() has to insert in the correct place, but removeMin() just takes the first element).
Strictly speaking, we should use an array with an extra index representing the first used position, like we did to implement queues, in order for removeMin() to be efficient.

## Bonus exercises

### B1. A data structure for medians

We use a class with these fields:

- a *max-heap* containing the median and all items smaller than the median,
- a *min-heap* containing all items larger than the median.

The median is the maximum element of the max-heap.
The two heaps must always have the same size (give or take one element – we allow the max-heap to be one bigger than the min-heap – this will happen if the collection has an odd number of items, and the median is then the maximum element of the max-heap).

<details markdown=block style="margin-bottom: 16px"><summary markdown=span>*Click here to see a more detailed implementation for multisets:*</summary>
```python
class MedianCollection
    // Contains the median and all items less than the median.
    // Size is either equal to or one more than secondHalf.size().
    firstHalf : MaxHeap

    // Contains all items greater than the median.
    secondHalf : MinHeap

    add(x):
        // Add the item to the correct heap, depending on whether it's less than the median or not.
        // Special case: If firstHalf is empty, then secondHalf must also be empty and so the collection is empty.
        // In that case, x will become the median and so we add it to firstHalf.
        if firstHalf.size() == 0 or x < getMedian():
            firstHalf.add(x)
        else:
            secondHalf.add(x)

        // Rebalance sizes if one of the heaps is too big.
        if firstHalf.size() > secondHalf.size()+1:
            secondHalf.add(firstHalf.removeMax())
        else if firstHalf.size() < secondHalf.size():
            firstHalf.add(secondHalf.removeMin())

    getMedian() -> Item:
        return firstHalf.getMax()

    removeMedian() -> Item:
        median = firstHalf.removeMax()
        // Rebalance sizes if firstHalf is now too small
        if firstHalf.size() < secondHalf.size():
            firstHalf.add(secondHalf.removeMin())
        return median
```
</details>

### B2. Implement a priority queue using a red-black BST

Use a red-black BST plus a field *currentMax* containing the current maximum item.
max() just returns *currentMax*.
All other operations update the red-black BST, search for the maximum item in the BST and update *currentMax* with that item.

### B3. Data structure with insert and min

Just have a single field *currentMin* containing the current minimum:

- `min()` returns *currentMin*
- `insert(x)` sets *currentMin* = x if x < *currentMin*
