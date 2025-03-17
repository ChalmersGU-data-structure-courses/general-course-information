# Exercise solutions: Complexity, part A

Here are suggested solutions to the exercises about complexity, part A.

## Core exercises (part A)

### A1. Asymptotic time complexity

1. Linear, $O(n)$: do a linear search over the array.
2. Logarithmic, $O(log(n))$: use binary search.
3. Constant, $O(1)$: increase the length of the array by one and add the element to the end.
4. Linear, $O(n)$: in the worst case, the element needs to be inserted at the front, requiring all other elements to move one step further.

### A2. Orders of growth

- $3 n^3 + 2 n^2 + 199 \in O(n^3)$
- $3 n^3 – 2 n^2 – 199 \in O(n^3)$
- $3 n^3 \cdot 2 n^2 \cdot 199 \in O(n^5)$
- $3 n^3 / 2 n^2 / 199 \in O(n)$
- $(n + 2 n^2)(2*n* + 3 n^2) \in O(n^4)$
- $(n + 2 n)(2 \log_2(n) + 3 \log_2(n)) \in O(n log(n))$

### A3. Asymptotic complexities of code fragments

- **f1**.
  The loop runs *n* times.
  In each iteration, the result increases by one.
  Thus, $T(n) = n \in O(n)$ (linear complexity).

- **f2**.
  The outer loop runs *n* times.
  In each iteration, the inner loop runs *n*–1 times.
  In each iteration, the result increases by one.
  Thus, $T(n) = n(n–1) \in O(n^2)$ (quadratic complexity).

- **f3**.
  The outer loop runs *n* times, ranging over *i* = 1, 2, …, *n*.
  In each iteration, the inner loop runs *i* times, which is (*n*+1)/2 on average.
  In each iteration, the result increases by one.
  In total, this increases the result by 1 + 2 + … + *n* = (*n*+1)/2 + (*n*+1)/2 + … + (*n*+1)/2 = *n*(*n*+1)/2.
  Thus, $T(n) = n(n+1)/2 \in O(n^2)$ (quadratic complexity).

  - *Note*.
    The complexity of the sum 1 + 2 + … + *n* can be determined without knowing the closed formula for it: $T(n) = 1 + 2 + \ldots + n \leq n ∙ n = n^2 \in O(n^2)$.

- **f4**.
  The outer loop runs ⌊*n*/4⌋ times.
  In each iteration, the middle loop runs ⌊*n*/9⌋ times, and in each of its iterations, the inner loop runs ⌊*n*/25⌋ times.
  Thus, $T(n) = \lfloor\frac{n}{4}\rfloor \cdot \lfloor\frac{n}{9}\rfloor \cdot \lfloor\frac{n}{25}\rfloor \leq \frac{n^3}{4 \cdot 9 \cdot 25} \in O(n^3)$.

- **f5**.
  The first loop runs *n* times; in each iteration, the result increases by one.
  The same happens with the second loop, except it runs *n*+1 times.
  Thus, $T(n) = n + (n+1) \in O(n)$ (linear complexity).

- **f6**.
  Let us first look at the nested loops at the start.
  It is the same as in **f3**, so it runs *n*(*n*+1)/2 times.
  The loop at the end runs *n* times, so it increases the final result by *n*.
  Thus, $T(n) = n(n+1)/2 + n \in O(n^2)$ (quadratic complexity).

### A4. Complexity of sorting algorithms

- Insertion sort has worst-case complexity $O(n^2)$ and average-case complexity $O(n^2)$.

- Merge sort has worst-case complexity $O(n \log(n))$ and average-case complexity $O(n \log(n))$.

- Quicksort has worst-case complexity $O(n^2)$ and average-case complexity $O(n \log(n))$, assuming a uniform distribution of input orderings.
  An elegant proof can be [found here](https://en.wikipedia.org/wiki/Quicksort#Using_a_binary_search_tree).

### A5. Checking for duplicates

In a sorted array, duplicate elements appear in right after one another.
So to check for duplicates, it suffices for 0 ≤ *i* < *n*–1, to check if **a**[*i*] equals **a**[*i*+1].

### A6. Print elements from two sorted arrays

Here is a rough sketch of the program:

1. Call the arrays **a** and **b**.
2. Initialize indices *i* for **a** and *j* for **b**.
3. Loop until one of the indices *i* and *j* reaches the end of its array:
    - if **a**[*i*] is equal to **b**[*j*], then print it and increase both *i* and *j*,
    - otherwise, increase the index of the array with the lower element.

We leave the details of actually turning it into a working program as an exercise for you!
Regarding the two questions:

- This program is very similar to the merging step in merge sort.
- The difference is that in merge sort we keep all elements, but here we only keep the ones that are equal.

### A7. Deletion from a dynamic array

See the lecture slides for Stacks & Queues.

### A8. Asymptotic complexities of code fragments

- **f7**.
  The outer loop runs $\lfloor\log_2(n) + 1\rfloor$ times, and the inner loop runs *n* times.
  In total, $T(n) = \lfloor\log_2(n) + 1\rfloor n \in O(n \log(n))$.

- **f8**.
  The outer loop ranges over $i = 1, 2, 2^2, 2^3, \ldots, 2^m$ where *m* is maximal such that $2^m \leq n$.
  This means $m = \lfloor\log_2(n)\rfloor$, so the outer loop runs $1 + m = 1 + \lfloor\log_2(n)\rfloor$ times.
  In each iteration, the inner loop runs $n^2$ times.
  In each iteration, the result increases by one.
  Thus, $T(n) = (1 + \lfloor\log_2(n)\rfloor) n^2 \in O(n^2 \log(n))$.

- **f9**: (This one is trickier that it seems)

    - The outer loop runs $\lfloor\log_2(n) + 1\rfloor \in O(\log(n))$ times.
    - The inner loop is a bit more tricky, it runs *i* times, where the value of *i* varies with every execution of the outer loop.
      It runs 1 time the first time, 2 times the second time, then 4 times, then 8 times, and so on.
      In total, it is called $\lfloor\log_2(n)\rfloor + 1$ times (since it is controlled by the outer loop).
      So in total, the innermost loop body runs the following number of times: $T(n) = 1 + 2 + 4 + 8 + \ldots + 2^{\lfloor\log_2(n)\rfloor}$.
    - Now, to compute the first part of this expression, which is a geometric progression, we use the following formula: $1 + r + r^2 + \ldots + r^{m-1} = (r^m – 1) / (r – 1)$ for *r* ≠ 1.
    - Substituting *r* = 2 and $m = \lfloor\log_2(n)\rfloor + 1$, we get $T(n) = (2^{\lfloor\log_2(n)\rfloor + 1} – 1) / (2 – 1) = 2^{\lfloor\log_2(n)\rfloor + 1} – 1.
    - Now, $2^{\lfloor\log_2(n)\rfloor + 1} – 1$ s within a constant factor (at most 2) of $2^{\log_2(n)} = n$.
    - So $T(n) \in O(n)$, and this is sharp (i.e. T(*n*) and *n* have the same the order of growth in *n*: linear).
