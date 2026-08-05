# Exam topics
{:.no_toc}

Here is a list of the main topics you should know for the exam, and also what you do not need to know.

* TOC
{:toc}

***Note***:
The chapter and section references refer to the [online course book](https://chalmersgu-data-structure-courses.github.io/dsabook/).
In general you should know *all book sections that do not have an asterisk* after the section number, including things that are not mentioned below.
In other words, the list below does not detail everything you need to know.

***Another note***:
An exam question (in particular an advanced one) may still touch on a topic listed as not required to know, or not covered by the course book.
But if that happens, solving the question does not require prior knowledge of that topic.

***Note for old students***:
This list is sometimes updated, so there might be differences from when you took the course!
If you plan to write a re-exam, please make sure you know all topics in this list, even if it was not part of your course instance.

## Algorithms and programming

### Searching in an array or a list (ch. 1)
- (1.3) Linear search in an array and in a linked list
    - how to do it, using a loop
    - linear complexity
- (1.3) Binary search in a sorted array
    - how to do it, with and without recursion
    - logarithmic complexity

### Sorting an array (chs. 2 and 4)
- (2.1) Terminology: *stable*, *adaptive* and *in-place* sorting algorithms
- (2.2) Comparing values
- (2.3--2.6) Insertion sort, selection sort, bubble sort
    - how to loop and insert/select elements
- (4.1) Recursion and divide-and-conquer
- (4.2) Mergesort
    - how to merge, how to split, how to recurse
- (4.3) Quicksort
    - pivot selection strategies you should know: first element, random element, median of three
    - why the pivot is crucial, why selecting the first element can be a bad strategy
    - how to partition, how to recurse
- (4.4) Know their asymptotic complexity
    - in the worst case / average case / on an already sorted array
    - linear, linearithmic or quadratic, depending on algorithm
- ***You do not need to know***:
    - timsort, bottom-up merge sort, run-based merge sort, 2-pivot quicksort, Tukey's ninther
    - which algorithms are stable and why this is an advantage

### Algorithms on graphs (ch. 12)
- (12.1, 12.7) Graph terminology and implementation
- (12.2) Graph traversal algorithms
- (12.3) Shortest-path problems and Dijkstra's algorithm (uniform-cost search)
- (12.4--12.5) Minimum spanning trees, and Prim's and Kruskal's algorithms
- See [the graphs section](#graphs-properties-features-and-algorithms) below

### Solving coding problems (no specific chapter or section)
- Given a problem, knowing which algorithm to use
- Given some simple code, figuring out what it does
- Given some code with holes, fill in the holes so that it works
- Given some code with an error, correct the bug
- Know the pseudocode for some basic algorithms
- Describe an algorithm using pseudocode (choosing your own syntax)
- Given a design for a data structure, figuring out how to implement a simple operation
- Using stacks, queues, sets, maps (including sorted sets and maps), priority queues and graphs in programs
- Combining basic data structures into the data structures you need in a program (e.g., that a multimap can be implemented as a map from keys to sets of values, or how to implement a sparse matrix)


## Abstract data types and data structures

### Abstract data types (ADTs, chs. 1, 8)
- (1.5) The main ADTs: stacks, queues and lists; priority queues; sets and maps, sorted sets and maps; graphs
- (chs. 6, 8--13) What ADTs can be implemented by what data structures
- (ch. 8) Naive, array-based implementations of the main ADTs
    - why they are inefficient, and why we need better alternatives
- Given a problem, knowing which ADT to use

### Data structures to know (chs. 1, 6, 9--12)
- Given a problem, knowing which data structure to use
- What data structures can be used to implement what ADTs
- The main data structures:
    - (ch. 6) Sequences: arrays, dynamic arrays, linked lists, stacks, queues
    - (ch. 9) Priority queues: binary heaps, meldable heaps
    - (ch. 10) Search trees: binary search trees, 2-3 trees, AVL trees
    - (ch. 11) Hash tables: separate chaining, open addressing (with linear probing)
    - (ch. 12) Graphs: undirected, directed, weighted, unweighted

### Sequences: dynamic arrays, linked lists, stacks, queues (ch. 6)
- (6.1--6.5) Stacks, queues
    - how to implement them using a dynamic array, or a linked list
    - implementing a circular queue in an array
- (6.2, 6.5) Linked lists
    - what the nodes look like
    - how to add an element, how to delete an element, how to search for an element
- (6.3--6.5) Arrays, dynamic arrays
    - how to add an element, how to look up an element, how to remove an element
    - how to resize, when to resize (only for dynamic arrays)
- (7.1--7.2) Asymptotic amortised complexity
    - for adding and removing, for accessing a position
    - implicit amortisation: you may assume that adding to the end of a dynamic array takes constant time, O(1)

### Rooted trees in general: properties (ch. 9)
- (9.1) Terminolgy: size and height of a tree; balanced, full, perfect and complete tree
    - that the height of a balanced tree is logarithmic in its size
- (9.1) Traversing trees: preorder, inorder, postorder; DFS, BFS
- (9.2) How to represent and implement trees
- (10.1) That an unbalanced tree can in the worst case be similar to a linked list

### Priority queues: binary heaps, meldable heaps (ch. 9)
- (8.2) How priority queues are used
- (9.4) What the heap property is
- (9.5) Binary heaps
    - complete binary trees, and how to store them in a dynamic array
    - how to *delete-min*, how to *insert*
    - how to *sink*/*bubble-down* and *swim*/*bubble-up*
    - asymptotic complexity of operations
- (9.6) Meldable heaps
    - how to define *insert* and *delete-min* in terms of *meld*
    - that meldable heaps are unbalanced, and why

### Search trees: BSTs, 2-3 trees, AVL trees (ch. 10)
- (10.1) Trees without balancing:
    - binary search trees (BST)
    - how the tree nodes look
    - how to insert, search, delete
    - how to find the minimum or maximum
    - examples when a BST becomes unbalanced (e.g., inserting nodes in order)
- (10.2--10.4) Self-balancing trees
    - tree rotations
    - AVL trees
    - 2-3 trees and B-trees
    - how the tree nodes look
    - how to insert (including rebalancing), how to search
- (10.1--10.4) Asymptotic complexity of insertion and searching
    - linear in the height of the tree
    - hence, logarithmic O(log(*n*)) for balanced trees, and linear O(*n*) for unbalanced trees
- (9.1) Traversing a tree
    - preorder, inorder, postorder; DFS, BFS
- ***You do not need to know***:
    - red-black trees
    - how to delete from a self-balancing tree (but you do need to know for an ordinary BST)
    - how to implement the ordering-based operations other than min and max (such as range queries, successor, predecessor, etc.)
    - but you do need to be able to use these operations in your programs

### Hash tables: separate chaining, open addressing (ch. 11)
- (11.1) That hash tables are not ordered
- (11.2) Separate chaining
    - how to insert, look up, delete a value
- (11.3, 11.5) Open addressing (with linear probing)
    - how to insert and look up a value
    - lazy deletion
- (11.4) How to resize, when to resize
    - that the hashing has to be redone after resizing
- (11.1, 11.6--11.7) Hash functions
    - what is a good / bad hashing function
    - What is the load factor
- (11.7) Asymptotic complexity
    - for insertion, lookup, deletion
    - if you have a good hash function, or a bad one
- (11.7) How to implement hash tables
- ***You do not need to know***:
    - probing variants other than linear probing
    - other ways of deleting in an open addressing hash table than lazy deletion
    - cryptographic hash functions or similar

### Graphs: properties, features and algorithms (ch. 12)
- (12.1) Terminology: (un)directed, (un)weighted, (a)cyclic, sparse/dense graphs, vertices, edges, paths, etc.
- (12.2) Searching in graphs / graph traversal
    - generic graph search
    - depth-first search (DFS)
    - breadth-first search (BFS)
    - that DFS/BFS solves the reachability problem
- (12.3) Shortest-path problems
    - what is a shortest path tree (from a given starting vertex)
    - Dijsktra's algorithm (uniform-cost search) for weighted graphs
    - that Dijkstra builds the shortest path tree in a weighted graph
    - that BFS builds the shortest path tree in an unweighted graph
- (12.4--12.5) Minimum-spanning trees (MST)
    - what is a spanning tree, and an MST; that they only exist for undirected graphs
    - Prim's algorithm and Kruskal's algorithm
- (12.6) Asymptotic complexities of the above algorithms
    - in terms of the size of the graph
    - for sparse graphs, this is equivalently in terms of the number of vertices
- (12.7) Representation and implementation: Adjacency lists, adjacency matrices
- ***You do not need to know***:
    - the algorithms by Bellman-Ford, Kusaraju, etc
    - the difference between the "lazy" and the "eager" versions of Prim and Dijkstra
    - A* search
    - Hamilton cycles, Euler circuits


## Algorithm analysis (chs. 3, 5, 7)


### Order of growth
- (3.4, 5.1--5.2) The definition of order of growth, O/Ω/Θ-notation
- (3.6) Simplifying order of growth
- (3.6, 5.1) The most important order-of-growth classes:
    - names for them (constant, logarithmic, linear, linearithmic (linear times logarithmic), quadratic, cubic, exponential)
    - how they compare
    - negligible growth: O(1) < O(log<sub>2</sub>(*n*)) = O(log<sub>10</sub>(*n*)) = O(log(*n*<sup>2</sup>)) = O(log(*n*)) < O(log(*n*)<sup>2</sup>)
    - acceptable growth for big *n*: O(*n*) < O(*n* log(*n*))
    - growing fast: O(*n*<sup>2</sup>) < O(*n*<sup>2</sup> log(*n*)) < O(*n*<sup>3</sup>)
    - growing too fast except for tiny *n*: O(2<sup>*n*</sup>) < O(10<sup>*n*</sup>) < O(*n*!)
- (5.1) How to add and multiply complexity classes

### Complexity: definitions, variations
- (3.1--3.2) Problems, algorithms, and invariants
- (3.3) Different measures
    - different kinds of cost: time (the default), space, number of certain operations (e.g., comparisons)
    - different kinds of complexity parameters ("in terms of […]"): input size (most common), output size, an integer argument, number of elements in data structure
- (3.5) Basic ways of handling cost variation between inputs with the same value of the chosen complexity parameter (e.g., same size):
    - worst case (the default)
    - average case: average over all possible inputs (example use case: analysing quicksort)
    - best case (never used)
- (7.1) Modifications to the notion of complexity:
    - amortised complexity: instead of measuring a single operation, average over **sufficiently long sequences** of operations (example use case: analysing dynamic arrays)
    - expected complexity: average over **all random choices** made in the algorithm (only relevant for randomised algorithms; example use case: quicksort with randomised pivot choice)
    - the difference between different kinds of averaging in complexity: average-case, amortised, expected. (*Test yourself*: these modifiers are all independent from each other. Can you make sense of combinations?)
- ***You do not need to know***:
    - how to analyze expected complexity

### Asymptotic complexity: how to analyse it
- (3.4) That asymptotic complexity (sometimes called *complexity class*) is the *order of growth* of the complexity function
- (3.6) Given a simple algorithm, how to determine its asymptotic complexity
    - example technique: deriving upper bounds for the asymptotic complexity of loops and sequences
- The asymptotic complexities of all the important data structures and algorithms in the course (see the cheat sheet below)
    - more importantly, how to derive them (so that you don't have to remember them!)
    - this includes the recursive algorithms merge sort and quicksort, and the amortised complexity of operations on dynamic arrays
- (5.4) Misconceptions:
    - the difference between complexity classes and speed/performance
    - the difference between saying "X has/is of complexity *f*(*n*)" (O(*f*(*n*)) and "the complexity class of X is *f*(*n*)" (Θ(*f*(*n*))))
- ***You do not need to know***:
    - advanced mathematics to evaluate complexity classes such as integral-based reasoning
    - probabilistic reasoning to determine the average-case complexity class
    - finding the asymptotic complexity of recursive programs of unfamiliar structure
    - optimality of comparison-based searching and sorting

### Complexity cheat sheet
**Life hack**: Do not memorise the below asymptotic complexities. Instead, focus on how the algorithms and data structures work. If you understand that, you can regenerate the asymptotic complexities on demand. So just use the below to double-check what you got.

- Binary search in a sorted array: logarithmic O(log(*n*))
- Linear search: linear O(*n*)
- Selection sort:
    - quadratic O(*n*<sup>2</sup>) (independent of input)
- Insertion sort:
    - quadratic O(*n*<sup>2</sup>)
    - linear O(*n*) for sorted lists
- Merge sort:
    - linearithmic O(*n* log(*n*)) (independent of input)
- Quicksort:
    - worst-case quadratic O(*n*<sup>2</sup>)
    - average-case linearithmic O(*n* log(*n*))
    - expected linearithmic O(*n* log(*n*)) if using a random pivot
    - quadratic O(*n*<sup>2</sup>) on sorted lists, if using the take-first pivot selection strategy
- Dynamic arrays:
    - appending an element at the end:
        - worst-case linear O(*n*) (this is when the array has to be resized)
        - amortised constant O(1)
    - constant O(1) for accessing a given index (position)
    - worst-case linear O(*n*) for finding an element
    - worst-case logarithmic O(log(*n*)) for finding an element in a sorted array (binary search)
- Linked lists:
    - constant O(1) for adding an element at the front
    - worst-case linear O(*n*) for finding an element, or looking up an index
- Hash tables (searching, adding and deleting):
    - worst-case linear O(*n*)
    - amortised average-case constant O(1) (needs good hash function)
    - it is amortised because we are using a dynamic array behind the scenes
- BSTs (searching, adding and deleting):
    - worst-case linear O(*n*)
    - average-case logarithmic O(log(*n*)) (for "well-behaved input")
    - linear O(*n*) if the elements are added in sorted order
- Self-balancing search trees (AVL tree, 2-3 tree):
    - worst-case logarithmic O(log(*n*))
- Binary heaps (adding, removing the minimum):
    - worst-case logarithmic O(log(*n*))
- Graph algorithms (Kruskal, Prim, UCS/Dijsktra):
    - worst-case linearithmic O(*n* log(*n*)) in size *n* of the graph
    - here, the size n is defined as *n* = \|V\| + \|E\| (we can also use max(\|V\|, \|E\|))
    - for sparse graphs, we can also take *n* = \|V\|
