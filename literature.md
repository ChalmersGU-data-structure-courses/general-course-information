# Reading material and other useful resources

The main course book is [our adaptation of the OpenDSA interactive course book](https://chalmersgu-data-structure-courses.github.io/dsabook/).

For doing the labs you will want to look up the library documentations for [Java](https://docs.oracle.com/en/java/javase/17/docs/api/index.html) or [Python](https://docs.python.org/3/library/index.html).

## Course book content, and optional sections

Here is a quick summary of the chapters in the course book.
Everything except where noted is compulsory material!

1. Introduction
    - motivation, background knowledge, abstract data types, and binary search

2. Algorithm analysis, part 1: Introduction
    - terminology, growth rates, asymptotic analysis, binary search

3. Sorting, part 1: Simple algorithms
    - terminology, selection sort, insertion sort
    - **optional**: 3.4 Bubble sort

4. Sorting, part 2: Divide-and-conquer algorithms
    - divide-and-conquer algorithms, mergesort, quicksort

5. Algorithm analysis, part 2: Theory
    - upper and lower bounds, big-O notation and others
    - **optional**: 5.3.1 Case study: Lower bounds for sorting

6. Stacks, queues, and lists
    - stacks, queues, linked lists, dynamic arrays, priority queues
    - **optional**: 6.9 Double-ended queues

7. Algorithm analysis, part 3: Advanced theory
    - space complexity, amortised analysis, dynamic arrays
    - **optional**: 7.4 Recurrence relations, 7.5 Multiple parameters

8. Trees
    - binary trees, general trees, traversing trees

9. Priority queues and heaps
    - the heap property, binary heaps, heapsort
    - **optional**: 9.5 Case study: Hoffman coding

10. Sets and maps
    - sets, maps, multimaps, sorted sets and maps

11. Search trees
    - binary search trees (BST), self-balancing trees, AVL trees, 2/3-trees
    - **optional**: 11.4 Splay trees, 11.5 Disjoint sets, union/find, 11.6 Skip lists

12. Hash tables
    - hash functions, separate chaining, open addressing, algorithmic complexity attacks
    - **optional**: 12.8 Different probing strategies, 12.11 Bucket hashing

13. Graphs
    - definitions and properties, implementations, traversing graphs,
      minimum spanning trees (MST), MST algorithms (Prim's and Kruskal's),
      shortest-path problems, Dijkstra's shortest-path algorithm
    - **optional**: 13.10 Specialised algorithms on weighted graphs

## Interactive visualisation tools

There are several tools available for visualising how different data structures and algorithms work.
Our favourites are of course developed by ourselves :).

- [Very smooth and responsive visualisations](https://chalmersgu-data-structure-courses.github.io/dsvis/).
  Currently only for a couple of data structures: search trees and binary heaps.
- [Not as modern visualisations](https://chalmersgu-data-structure-courses.github.io/visualization/).
   Many many data structures and algorithms – this is an updated version of a library originally created by [David Galles](https://www.cs.usfca.edu/~galles/), University of San Francisco.

Here are some other favourites:

- [Gnarley trees](https://github.com/ChalmersGU-data-structure-courses/alg-vis): covers most data structures from the course, but no standalone algorithms.
- [VisuAlgo](https://visualgo.net/en): more polished than the Gnarley trees, but does not cover as many data structures.

## Supplementary material

Data structures is a subject that is taught in a similar way all over the world.
This means that there are loads of books about data structures and algorithms.
Most of them are okay and present roughly the same material as we do in this course.
If you get your hands on a second-hand course book, it's probably good enough.
But be prepared that there might be differences both in how they are organised and what content is included.

We recommend [Algorithms (2014)](https://www.pearson.com/en-us/subject-catalog/p/algorithms/P200000000597/9780137459575) by Robert Sedgewick and Kevin Wayne as supplemental reading, because they have better explanations of the data structures and algorithms.
And lots of examples and exercises.
It's enough to only read part 1, which is [a very affordable e-book](https://www.google.com/search?q=ISBN+9780133799101).

The book has [an excellent website](https://algs4.cs.princeton.edu/home/) which is well worth a look.
You can find short explanations of each data structure from the book (under the chapter headings on the left of the page), as well [a cheatsheet](https://algs4.cs.princeton.edu/cheatsheet/), and [references to classic papers](https://algs4.cs.princeton.edu/references/).

## Free books

Here are some course-related books that are available free online.
You do not need to read them to pass the course, but if you want to go deeper then the first book in particular is great!

- The [Algorithm Design Manual](https://link.springer.com/book/10.1007/978-1-84800-070-4), by Steven S Skiena.
  The e-book is free at the Chalmers library with your Chalmers CID.
  A very readable book that teaches you how to design fast algorithms using appropriate data structures, and how to think about algorithm design.
  A cool part is the "War Stories" where the author describes real-world problems they had to solve and the thought process that led them to an algorithmic solution.

- [Open Data Structures](http://opendatastructures.org/) by Pat Morin.
  A free textbook that covers lots of the course material.
  We found it harder to understand than Sedgewick and Wayne, but it is useful as a reference.
  It has separate editions for Java, Python and C++.

- **Advanced**: [Algorithms](http://jeffe.cs.illinois.edu/teaching/algorithms/) by Jeff Erickson.
  A free algorithms textbook. Very well-written, but doesn't match up well with the course contents (it's made for a more advanced course).
  Still, well worth a look if you want to learn more about algorithm design.

## Non-free but excellent books

The books in this section are not part of the course, but are great reads if you want to learn more.
All of them can be found in the Chalmers library.

- [Programming Pearls](https://web.archive.org/web/20150202033425/http://www.cs.bell-labs.com/cm/cs/pearls/index.html) by Jon Bentley.
  This is a real classic book of computer science, and very relevant to the course.
  It’s a collection of short articles, each of which presents a creative and elegant solution to some programming problem.
  The solution often involves clever use of some data structure.
  The book is also: a) well written, b) quite short and c) quite cheap.
  If you read it you will become a better programmer! It is available online with your Chalmers CID.

- **Advanced**:
  We don't explicitly cover data structures in functional languages (though any structure that does not use arrays or cycles of pointers usually translates well, for example trees).
  If you want to learn about advanced functional data structures, the classic reference is Chris Okasaki’s book, [Purely Functional Data Structures](https://www.google.com/search?q=chris+okasaki+purely+functional+data+structures).

- **Advanced**:
  We only scratch the surface of the mathematics of algorithm analysis (e.g. solving recurrence relations).
  It's really a whole subfield of discrete mathematics with many cool techniques.
  If you want to learn much, much, much more about it, a good book is [Concrete Mathematics](https://en.wikipedia.org/wiki/Concrete_Mathematics) by Ronald Graham, Donald Knuth and Oren Patashnik.
  It's hard work but rewarding!
