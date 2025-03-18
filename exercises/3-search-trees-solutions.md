# Exercise solutions: Search trees

Here are suggested solutions to the exercises about search trees.

## Core exercises

### A1 and A2. Insert values into a tree

- For binary search trees, try the [BST visualisation](https://chalmersgu-data-structure-courses.github.io/dsvis/collections.html?algorithm=BST).
- For AVL trees, try the [AVL visualisation](https://chalmersgu-data-structure-courses.github.io/dsvis/collections.html?algorithm=AVL).
- For 2-3 trees, try the [B-tree visualisation](https://chalmersgu-data-structure-courses.github.io/dsvis/collections.html?algorithm=BTree) and choose the option "Max degree = 2/3-tree".

What you should notice is that for question **A2**, the binary search tree becomes extremely unbalanced, while the others do not because they are self-balancing!

### A3. Implement the following functions on BSTs

- `smallest(tree) -> int`:
  The smallest value is in the leftmost node, so go left until there are no more left children.

- `delete_minimum(tree) -> BST`:
  If the leftmost node is a leaf, then we can just delete it.
  Otherwise it must have one single right child (why?).
  Now, reassign the parent of the smallest node to point to the right child.

- `delete(tree, value) -> BST`:
  See the course book and the lecture slides for an implementation.

- `bst_to_list(tree) -> list of int`:
  Call yourself recursively with the left child, and with the right child.
  Then return the concatenation, but don't forget to put the root node value in between the two lists.

### A4. Implement set operations

```python
union(s1, s2):
    for each x in s2:
        s1.add(x)

intersection(s1, s2):
    for x in s1:
        if not s2.contains(x):
            s1.remove(x)

difference(s1, s2):
    for x in s2:
        s1.remove(x)
```

**Bonus part**:
We will only show the solution for difference.

Here are two ways to implement set difference, with different complexities:

- Method 1: for each key k in s<sub>2</sub>, delete k from s<sub>1</sub>.
- Method 2: for each key k in s<sub>1</sub>, if k is found in s<sub>2</sub> then delete k from s<sub>1</sub>.

Suppose that s<sub>1</sub> has size M and s<sub>2</sub> has size N (note different notation from the question because we use capital N and M).
Then method 1 takes time proportional to N log(M), while method 2 takes time proportional to M log(max(M, N)).
Therefore, the solution is:

- If s<sub>1</sub> is bigger than s<sub>2</sub>, use method 1, otherwise use method 2.
  (Note: if we use method 2 then s<sub>1</sub> is smaller than s<sub>2</sub> and so max(M, N) = N.

### A5. Sorting using a BST

- a)
  It's not a sorting algorithm because if the input has duplicates, it discards them.
  (However, that may be fixed by allowing duplicates in a BST.)
- b)
  It takes O(n log(n)) time, where n is the size of the input.
  Shuffling takes O(n) time, there are n insertions which take O(log(n)) time each, and the in-order traversal takes O(n) time.
- c)
  Shuffling makes sure that the BST we create is balanced.
  Inserting keys in a random order produces almost surely a BST with O(log(n)) height, so the insertions take O(log(n)) time.
  Without this step, sorting e.g. an input that was already sorted would take quadratic time (n insertions, each taking O(n) time).

### A6. Multisets and multimaps

**For a multiset**: use a balanced BST map where the values are integers.
Here are some possible operations:

- `count(x) -> int`: get the count of a particular element.
  (Implementation: look up the key in the BST, return 0 if not found.)

- Set-like operations, such as union and intersection.
  Typically for multisets we say e.g. that if *S* contains *m* copies of a key *x*, and *T* contains *n* copies of *x*, then *S* ∪ *T* should contain *m+n* copies of *x*.

  - <p><details><summary><em>Click here to see a sketch of an implmeentation that does this:</em></summary>

    ```python
    union(other):
        for key in other.keys():
            if not this.contains(key):
                this.put(key, 0)
        this.put(key, this.get(key) + other.get(key)
    ```
    </details></p>

**For a multimap**: use a balanced BST where the values are sets.
Possible extra operations include:

- Iterating through all key-value pairs
- Taking the union or intersection of two multimaps
- `valuesFor(x) -> Set`: return all values associated with a particular key.
  (Implementation: look up the key in the BST, return the empty set if not found.)
- `contains(x, v) -> boolean`: check if a given key-value pair is in the multimap.
  (Implementation: look up the key in the BST to get a set of values, look up the value in that set.)

<p><details><summary><em>Click here to see a more detailed implementation for multisets:</em></summary>

```python
class Multiset:
    # e.g. using a map implemented using an AVL tree
    map = new AVLTree()

    add(x):
        if map.contains(x):
            count = map.get(x)
        else:
          count = 0
        map.put(x, count + 1)

    remove(x):
        if map.contains(x):
            count = map.get(x)
            if count == 1:
                map.remove(x)
            else:
                map.put(x, count - 1)

    count(x) -> int:
        if map.contains(x):
            return map.get(x)
        else:
            return 0

    contains(x) -> bool:
        return count(x) != 0

    # plus code for "union" from above
```
</details><p>

## Bonus exercises

To be done.
