# Exam topics
{:.no_toc}

Here is a detailed list what topics you should know for the exam, and also what you do not need to know. Grouped by categories:

* TOC
{:toc}

***Note***:
An exam question (particular advanced ones) may still touch on a topic not explicitly listed (or even listed as not required to know).
But if that happens, solving the question does not require prior knowledge of that topic.

***Another note***:
The chapter and section references refer to the [online course book](https://chalmersgu-data-structure-courses.github.io/dsabook/).

***Note for old students***:
This list is sometimes updated, so there might be differences from when you took the course!
If you plan to write a re-exam, please make sure you know all topics in this list, even if it was not part of your course instance.

## Algorithms and programming

### Sorting an array (chs. 3--4)
- (3.1) Terminology: *stable*, *adaptive* and *in-place* sorting algorithms
- (3.2) Comparing values
- (3.5--3.7) Insertion sort, selection sort
    - how to loop and insert/select elements
- (4.1) Recursion and divide-and-conquer
- (4.2--4.3) Mergesort
    - how to merge, how to split, how to recurse
- (4.4--4.5) Quicksort
    - pivot selection strategies you should know: first element, random element, median of three
    - why the pivot is crucial, why selecting the first element can be a bad strategy
    - how to partition, how to recurse
- (3.5.1, 3.6.1, 3.7, 4.2.2, 4.4.2) Know their asymptotic complexity
    - in the worst case / average case / on an already sorted array
    - linear, linearithmic or quadratic, depending on algorithm
- ***You do not need to know***:
    - timsort, bottom-up merge sort, run-based merge sort, 2-pivot quicksort, Tukey's ninther
    - which algorithms are stable and why this is an advantage

### Searching in an array or a list (ch. 1)
- (1.6) Linear search in an array and in a linked list
    - how to do it, using a loop
    - linear complexity
- (1.6, 2.8) Binary search in a sorted array
    - how to do it, with and without recursion
    - logarithmic complexity

### Algorithms on graphs (ch. 13)
- (13.4) Graph traversal algorithms
- (13.5--13.7) Prim's and Kruskal's algorithms
- (13.8--13.9) Dijkstra's algorithm (uniform-cost search)
- See [the graphs section](#graphs-properties-features-and-algorithms) below

### Solving coding problems (no specific chapter or section)
- Given a problem, knowing which algorithm to use
- Given some simple code, figuring out what it does
- Given some code with holes, fill in the holes so that it works
- Given some code with an error, correct the bug
- Know the pseudocode for some basic algorithms
- Describe an algorithm using pseudocode (choosing your own syntax)
- Given a design for a data structure, figuring out how to implement a simple operation
- Using stacks, queues, sets, maps (including ordered sets and maps), priority queues and graphs in programs
- Combining basic data structures into the data structures you need in a program (e.g., that a multimap can be implemented as a map from keys to sets of values, or how to implement a sparse matrix)


## Abstract data types and data structures

### Abstract data types (ADTs, chs. 6, 8--13)
- (1.7) The main ADTs: stacks, queues and lists; priority queues; sets and maps, ordered sets and maps; graphs
- (chs. 6, 8--13) What ADTs can be implemented by what data structures
- Given a problem, knowing which ADT to use

### Data structures to know (chs. 6, 8--13)
- Given a problem, knowing which data structure to use
- What data structures can be used to implement what ADTs
- The main data structures:
    - (ch. 6) Lists: arrays, dynamic arrays, linked lists, stacks, queues
    - (ch. 11) Search trees: binary search trees, 2-3 trees, AVL trees
    - (ch. 9) Priority queues: binary heaps
    - (ch. 12) Hash tables: separate chaining, linear probing
    - (ch. 13) Graphs: undirected, directed, weighted, unweighted

### Lists: dynamic arrays, linked lists, stacks, queues (ch. 6)
- (6.3--6.4) Linked lists
    - what the nodes look like
    - how to add an element, how to delete an element, how to search for an element
- (6.5--6.8) Arrays, dynamic arrays
    - how to add an element, how to look up an element, how to remove an element
    - how to resize, when to resize (only for dynamic arrays)
- (6.2--6.6) Stacks, queues
    - how to implement them using a dynamic array, or a linked list
    - implementing a circular queue in an array
- (7.3) Asymptotic complexity
    - for adding and removing, for accessing a position
    - implicit amortization: you may assume that adding to the end of a dynamic array takes constant time, O(1)

### Rooted trees in general: properties (ch. 8)
- (8.1) Size and height of a tree
- (8.1) Balanced tree, complete tree
- (8.1) That the height of a balanced tree is logarithmic in the size of the tree
- (11.2) That an unbalanced tree can in the worst case be similar to a linked list
- (8.3, 8.6) How to implement trees
- (8.4--8.6) Traversing, information flow

### Search trees: BSTs, 2-3 trees, AVL trees (ch. 11)
- (11.1) Trees without balancing:
    - binary search trees (BST)
    - how the tree nodes look
    - how to insert, search, delete
    - how to find the minimum or maximum
    - examples when a BST becomes unbalanced (e.g., inserting nodes in order)
- (11.2--11.3) Self-balancing trees
    - AVL
    - 2/3-trees
    - how the tree nodes look
    - how to insert (including rebalancing), how to search
- (11.1--11.3) Asymptotic complexity of insertion and searching
    - linear in the height of the tree
    - hence, logarithmic O(log(*n*)) for balanced trees
    - linear O(*n*) for general general trees
- (8.4) Traversing a tree
    - preorder, inorder, postorder
- ***You do not need to know***:
    - red-black trees
    - how to delete from a self-balancing tree (but you do need to know for an ordinary BST)
    - how to implement the ordering-based operations other than min and max (such as range queries, successor, predecessor, etc.)
    - but you do need to be able to use these operations in your programs

### Priority queues: binary heaps (ch. 9)
- (9.1) What the heap property is
- How priority queues are used
- (9.2) Binary heaps
    - how to store a binary heap in a dynamic array
    - how to delete-min, how to insert
    - asymptotic complexity of operations

### Hash tables: separate chaining, linear probing (ch. 12)
- (12.1, 12.10) Hash functions
    - what is a good / bad hashing function
    - What is the load factor
- (12.1) That hash tables are not ordered
- (12.3, 12.6) How to resize, when to resize
    - that the hashing has to be redone after resizing
- (12.3) Separate chaining
    - how to insert, look up, delete a value
- (12.5--12.7) Linear probing
    - how to insert and look up a value
    - lazy deletion
- (12.9) Asymptotic complexity
    - for insertion, lookup, deletion
    - if you have a good hash function, or a bad one
- ***You do not need to know***:
    - probing variants other than linear probing
    - other ways of deleting in an open addressing hash table than lazy deletion
    - cryptographic hash functions or similar

### Graphs: properties, features and algorithms (ch. 13)
- (13.1) Undirected / directed, unweighted / weighted
- (13.2) Adjacency lists, adjacency matrices
- (13.1) Features of graphs – what are…?
    - nodes (vertices), edges
    - paths, cycles
    - reachability
    - connected components
    - strongly connected components (for directed graphs)
    - DAGs
    - spanning trees, MSTs (for undirected graphs)
    - shortest path trees
    - sparse / dense graphs
- (13.4, 13.9) Searching in graphs
    - depth-first search (DFS)
    - breadth-first search (BFS)
    - uniform-cost search (UCS) (Dijsktra's algorithm) for weighted graphs
    - that DFS/BFS solves the reachability problem
    - that BFS builds the shortest path tree in an unweighted graph
    - that UCS/Dijkstra builds the shortest path tree in a weighted graph
- (13.5--13.7) Minimum-spanning trees
    - Prim's algorithm and Kruskal's algorithm
- (13.6, 13.7, 13.9) Asymptotic complexities of the above algorithms
    - in terms of the size of the graph
    - for sparse graphs, this is equivalently in terms of the number of nodes
- ***You do not need to know***:
    - the algorithms by Bellman-Ford, Kusaraju, etc
    - the difference between the "lazy" and the "eager" versions of Prim and Dijkstra
    - A* search
    - Hamilton cycles, Euler circuits


## Algorithm analysis (chs. 2, 5, 7)

### Order of growth (2.4--2.6)
- The definition of order of growth, O/Ω/Θ-notation
- Simplifying order of growth
- The most important order-of-growth classes:
    - names for them (constant, logarithmic, linear, linearithmic (linear times logarithmic), quadratic, cubic, exponential)
    - how they compare
    - negligible growth: O(1) < O(log<sub>2</sub>(*n*)) = O(log<sub>10</sub>(*n*)) = O(log(*n*)) < O(log(*n*)<sup>2</sup>)
    - acceptable growth for big *n*: O(*n*) < O(*n* log(*n*))
    - growing fast: O(*n*<sup>2</sup>) < O(*n*<sup>2</sup> log(*n*)) < O(*n*<sup>3</sup>)
    - growing too fast except for tiny *n*: O(2<sup>*n*</sup>) < O(10<sup>*n*</sup>) < O(*n*!)
- How to add and multiply complexity classes

### Complexity: definitions, variations (2.1--2.3, 5.1--5.4, 7.1--7.2)
- Different kinds of cost:
    - time (the default)
    - space
    - number of certain operations (e.g., comparisons)
- Different kinds of complexity parameters ("in terms of […]"):
    - input size (most common)
    - output size
    - an integer argument
    - number of elements in data structure
- Basic ways of handling cost variation between inputs with the same value of the chosen complexity parameter (e.g., same size):
    - worst case (the default)
    - average case: average over all possible inputs (example use case: analysing quicksort)
    - best case (never used)
- Modifications to the notion of complexity:
    - amortized complexity: instead of measuring a single operation, average over **sufficiently long sequences** of operations (example use case: analysing dynamic arrays)
    - expected complexity: average over **all random choices** made in the algorithm (only relevant for randomized algorithms; example use case: quicksort with randomized pivot choice)
- The difference between different kinds of averaging in complexity: average-case, amortized, expected. (*Test yourself*: these modifiers are all independent from each other. Can you make sense of combinations?)
- ***You do not need to know***:
    - how to analyze expected complexity

### Asymptotic complexity: how to analyse it (2.7--2.9)
- That asymptotic complexity (sometimes called *complexity class*) is the *order of growth* of the complexity function
- Given a simple algorithm, how to determine its asymptotic complexity
    - example technique: deriving upper bounds for the asymptotic complexity of loops and sequences
- The asymptotic complexities of all the important data structures and algorithms in the course (see the cheat sheet below)
    - more importantly, how to derive them (so that you don't have to remember them!)
    - this includes the recursive algorithms merge sort and quicksort, and the amortized complexity of operations on dynamic arrays
- Misconceptions:
    - the difference between complexity classes and speed/performance
    - the difference between saying "X has/is of complexity *f*(*n*)" (O(*f*(*n*)) and "the complexity class of X is *f*(*n*)" (Θ(*f*(*n*)))
- ***You do not need to know***:
    - advanced mathematics to evaluate complexity classes such as integral-based reasoning
    - probabilistic reasoning to determine the average-case complexity class
    - finding the asymptotic complexity of recursive programs of unfamiliar structure
    - optimality of comparison-based searching and sorting

### Complexity cheat sheet
**Life hack**: Do not memorize the below asymptotic complexities. Instead, focus on how the algorithms and data structures work. If you understand that, you can regenerate the asymptotic complexities on demand. So just use the below to double-check what you got.

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
        - amortized constant O(1)
    - constant O(1) for accessing a given index (position)
    - worst-case linear O(*n*) for finding an element
    - worst-case logarithmic O(log(*n*)) for finding an element in a sorted array (binary search)
- Linked lists:
    - constant O(1) for adding an element at the front
    - worst-case linear O(*n*) for finding an element, or looking up an index
- Hash tables (searching, adding and deleting):
    - worst-case linear O(*n*)
    - amortized average-case constant O(1) (needs good hash function)
    - it is amortized because we are using a dynamic array behind the scenes
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
