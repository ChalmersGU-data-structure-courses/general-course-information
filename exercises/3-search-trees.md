# Exercises: Search trees

**Note:**
The exercises are optional, but highly recommended.
If you are uncertain about any problem or want to discuss, write in the course discussion channel, or ask a teacher.

The exercises are divided into ***core*** and ***bonus***.
We recommend you try all the core exercises.
Try some of the bonus exercises if you want to learn more.

## Core exercises

**A1**.
Insert the values 2, 1, 4, 5, 9, 3, 6, 7 into an empty:

- binary search tree,
- 2-3 tree,
- AVL tree.

**A2**.
Insert the values 1, 2, 3, 4, 5, 6, 7, 8 into an empty:

- binary search tree,
- 2-3 tree,
- AVL tree.

**A3**.
Implement the following functions on BSTs:

- `smallest(tree) -> int`: return the smallest value in a BST.

  <p><details><summary><em>Hint:</em></summary>
  Where in a BST is the smallest value?
  </details></p>

- `delete_minimum(tree) -> BST`: delete the smallest value in a BST.

  <p><details><summary><em>Hint:</em></summary>
  There are two possibilities: either the smallest value is a leaf (which is a straightforward case), or it can be an inner node.
  If it is an inner node, how many children does it have, and what kind of children?
  </details></p>

- `delete(tree, value) -> BST`: delete a given value in a BST.

  <p><details><summary><em>Hint:</em></summary>
  See the course book and the lecture slides.
  </details></p>

- `bst_to_list(tree) -> list of int`: return the contents of a BST in sorted order.
  
  <p><details><summary><em>Hint:</em></summary>
  Make two recursive calls, and then figure out how to combine the results.
  </details></p>

You can implement in pseudocode or Java or Python, it's up to you.

**A4**.
Suppose we have a class `Set` which represents a set of items.
The following functions are defined for it:

- `add(set, item)`: adds an item to the set
- `remove(set, item)`: removes an item from the set
- `contains(set, item) -> boolean`: checks if an item is present in the set

By using `add`, `remove`, `contains`, and the `Set` iterator, show how to define functions that do set union, intersection, and difference. Specifically, define the following functions, either in code or pseudocode:

- `union(s1, s2)`: Afterwards, s<sub>1</sub> should contain the items that were previously in s<sub>1</sub> ∪ s<sub>2</sub>.
- `intersection(s1, s2)`: Afterwards, s<sub>1</sub> should contain the items that were previously in s<sub>1</sub> ∩ s<sub>2</sub>.
- `difference(s1, s2)`: Afterwards s<sub>1</sub> should contain the items that were previously in s<sub>1</sub> but not in s<sub>2</sub>.

Each operation takes two sets s<sub>1</sub> and s<sub>2</sub>, and stores the union/intersection/difference of the two sets in s<sub>1</sub>.

**Bonus part:**
Suppose that `Set` is implemented using a balanced BST.
Show how to implement `intersection` and `difference` so that their runtime is *O(n log(m))*, where *n* is the size of the *smaller* of the two sets `this` and `other`, and *m* is the size of the *larger* set.

<p><details><summary><em>Hint:</em></summary>
First check which of the sets is larger, then write code for that particular case.
</details></p>

**A5**.
Consider the following algorithm for sorting a list of keys:

1. Shuffle the list of keys.
2. Add each key in turn to a BST.
3. Do an in-order traversal of the BST to get the keys in ascending order.

Answer the following questions:

- a)
  This algorithm is almost a correct sorting algorithm, but not quite.
  What is the problem?
- b)
  What is the complexity of the algorithm?
- c)
  What is the purpose of shuffling the list of keys first?

**A6**.
Design a data structure representing a *multiset*: a set that can contain duplicates.
It's up to you what operations your data structure should support.

<p><details><summary><em>Hint:</em></summary>
Use a map; you do not need to implement the map but can just use an existing implementation.
</details></p>

Also design a data structure representing a *multimap*: a symbol table (map) where each key can be associated with multiple values.

## Bonus exercises

**B1**.
Describe an algorithm that finds the *successor* of a key in a BST: the key that comes directly after it in sorted order.
The runtime should be proportional to the height of the BST.

<p><details><summary><em>Hint:</em></summary>
Make the algorithm return *null* if the key is the largest one.
The algorithm is recursive (similar to the search algorithm) but there are extra cases depending on whether each recursive call returns *null* or not.
</details></p>

**Harder:**
Design an algorithm that, given a BST and two keys x and y, finds all keys between x and y in the BST (for example, returning them in a queue).
The runtime should be *O(log(N) + M)* for a balanced BST, where *N* is the size of the BST and *M* is the number of keys returned.

**B2**.
Define a function
```
isBST(node: Node) -> boolean
```
that takes a node and checks if the tree rooted at that node is a valid BST.

The simplest way to define this method potentially visits each node many times, and takes quadratic time on unbalanced tree.
Define a function
```
isBSTBetween(node: Node, min: Key, max: Key) -> boolean
```
that checks that a tree is a BST, *and* that all keys in it are `> min` and `< max`.
The arguments `min` and `max` can be `null`/`None`, in which case that part of the check is ignored.
The method should only visit each node in the tree once. Use this method to define a linear-time `isBST` method.

**B3**.
Design a data structure representing a *bidirectional map*: a symbol table where there is a one-to-one relationship between key and values - each key is associated with one value, and each value is associated with one key.
In addition to the usual symbol table operations it should provide a "reverse lookup" operation which takes a value and finds the corresponding key efficiently).
When inserting a key-value pair, any conflicting key-value pair should be removed.

<p><details><summary><em>Hint:</em></summary>
Use two balanced BSTs.
The code for adding a new key-value pair is a little tricky, so make sure to write down an invariant relating the two BSTs.
</details></p>

**B4**.
Suppose that we have a binary search tree where each node also contains a reference to its parent node.
Design an algorithm that performs an in-order traversal of the tree (e.g. printing out the nodes in ascending order), but *using a constant amount of extra memory*.
Note that the normal recursive algorithm for in-order traversal requires O(height of tree) extra memory because each recursive call consumes memory.

**B5**.
Learn about how 2-3 tree deletion works by reading these notes: <http://www.cs.princeton.edu/~dpw/courses/cos326-12/ass/2-3-trees.pdf>.

**B6**.
**Hard, very optional extra bonus question.**
A 2-3-4 tree consists of 2-nodes, 3-nodes and 4-nodes (a node with three values and four children).
Insertion in 2-3-4 trees uses a more efficent insertion algorithm called *top-down insertion*.
In top-down insertion, as you move down the tree looking for the insertion point, whenever you reach a 4-node you split it and absorb it into its parent (note that because we split all 4-nodes on the way down, the parent is always a 2- or 3-node so absorption is easy).
When we reach the leaf, we split it and insert the appropriate value.

- Describe in more detail the algorithm for inserting into a 2-3-4 tree using top-down insertion.
