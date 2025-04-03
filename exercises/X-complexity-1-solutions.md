# Exercise solutions: Complexity, part A

Here are suggested solutions to the exercises about complexity, part A.

## Core exercises (part A)

### A1. Asymptotic time complexity

1. Linear, O(*n*): do a linear search over the array.
2. Logarithmic, O(log *n*): use binary search.
3. Constant, O(1): increase the length of the array by one and add the element to the end.
4. Linear, O(*n*): in the worst case, the element needs to be inserted at the front, requiring all other elements to move one step further.

### A2. Asymptotic complexities of code fragments

- **f1**.
  The loop body runs *n* times.
  In each iteration, the result increases by one.
  Thus, T(*n*) = *n* ∈ O(*n*) (linear complexity).

- **f2**.
  The outer loop has *n* iterations.
  In each iteration, the inner loop body runs *n*–1 times.
  In each iteration, the result increases by one.
  Thus, T(*n*) = *n*(*n*–1) ∈ O(*n*<sup>2</sup>) (quadratic complexity).

- **f3**.
  The body of the outer loop runs *n* times, ranging over *i* = 1, 2, …, *n*.
  In each iteration, the inner loop body runs *i* times, which is (*n*+1)/2 on average.
  In each iteration, the result increases by one.
  In total, this increases the result by 1 + 2 + … + *n* = (*n*+1)/2 + (*n*+1)/2 + … + (*n*+1)/2 = *n*(*n*+1)/2.
  Thus, T(*n*) = *n*(*n*+1)/2 ∈ O(*n*<sup>2</sup>) (quadratic complexity).

  **Note**:
  The growth rate of the sum 1 + 2 + … + *n* can be determined without knowing the closed formula for it: T(*n*) = 1 + 2 + … + *n* ≤ *n* ∙ *n* = *n*<sup>2</sup> ∈ O(*n*<sup>2</sup>).

- **f4**.
  The outer loop has ⌊*n*/4⌋ iterations.
  In each iteration, the middle loop runs ⌊*n*/9⌋ times, and in each of its iterations, the inner loop body runs ⌊*n*/25⌋ times.
  Thus, T(*n*) = ⌊*n*/4⌋·⌊*n*/9⌋·⌊*n*/25⌋ ≤ *n*<sup>3</sup>/(4·9·25) ∈ O(*n*<sup>3</sup>).

- **f5**.
  The body of the first loop runs *n* times; in each iteration, the result increases by one.
  The same happens with the second loop, except it has *n*+1 iterations.
  Thus, T(*n*) = *n* + (*n*+1) ∈ O(*n*) (linear complexity).

- **f6**.
  Let us first look at the nested loops at the start.
  It is the same as in **f3**, so it runs *n*(*n*+1)/2 times.
  The body of the loop at the end runs *n* times, so it increases the final result by *n*.
  Thus, T(*n*) = *n*(*n*+1)/2 + *n* ∈ O(*n*<sup>2</sup>) (quadratic complexity).

### A3. Complexity of sorting algorithms

- Insertion sort has worst-case complexity O(*n*<sup>2</sup>) and average-case complexity O(*n*<sup>2</sup>).

- Merge sort has worst-case complexity O(*n* log(*n*)) and average-case complexity O(*n* log(*n*)).

- Quicksort has worst-case complexity O(*n*<sup>2</sup>) and average-case complexity O(*n* log(*n*)), assuming a uniform distribution of input orderings.
  An elegant proof can be [found here](https://en.wikipedia.org/wiki/Quicksort#Using_a_binary_search_tree).

### A4. Checking for duplicates

In a sorted array, duplicate elements appear in right after one another.
So to check for duplicates, it suffices for 0 ≤ *i* < *n*–1, to check if **a**[*i*] equals **a**[*i*+1].

### A5. Print elements from two sorted arrays

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

### A6. Deletion from a dynamic array

See the lecture slides for Stacks & Queues.

### A7. Asymptotic complexities of code fragments

- **f7**.
  The outer loop has [log<sub>2</sub>(*n*) + 1] iterations, and each time the inner loop body runs *n* times.
  In total, T(*n*) = [log<sub>2</sub>(*n*) + 1] *n* ∈ O(*n* log(*n*)).

- **f8**.
  The outer loop ranges over *i* = 1, 2, 2<sup>2</sup>, …, 2<sup>*m*</sup> where *m* is maximal such that 2<sup>*m*</sup> ≤ *n*.
  This means *m* = ⌊log<sub>2</sub>(*n*)⌋, so the outer loop has 1 + ⌊log<sub>2</sub>(*n*)⌋ iterations.
  In each iteration, the inner loop runs *n*<sup>2</sup> times.
  In each iteration, the result increases by one.
  Thus, T(*n*) = (1 + ⌊log<sub>2</sub>(*n*)⌋) *n*<sup>2</sup> ∈ O(*n*<sup>2</sup> log(*n*)).

- **f9**: (This one is trickier that it seems)

    - The body of the outer loop runs [log<sub>2</sub>(*n*) + 1] = O(log *n*) times.
    - The loop loop is a bit more tricky, it has *i* iterations, where the value of *i* varies with every execution of the outer loop body.
      It runs 1 time the first time, 2 times the second time, then 4 times, then 8 times, and so on.
      In total, it is called [log<sub>2</sub>(*n*)] + 1 times (since it is controlled by the outer loop).
      So in total, the innermost loop body runs the following number of times: T(*n*) = 1 + 2 + 4 + 8 + ... + 2<sup>[log<sub>2</sub>(*n*)]</sup>.
    - Now, to compute the first part of this expression, which is a geometric progression, we use the following formula: 1 + *r* + *r*<sup>2</sup> + ... + *r*<sup>*m*–1</sup> = (*r*<sup>*m*</sup> – 1) / (*r* – 1) for *r* ≠ 1.
    - Substituting *r* = 2, *m* = [log<sub>2</sub>(*n*)] + 1, we get T(*n*) = (2<sup>[log<sub>2</sub>(*n*)]+1</sup> – 1) / (2 – 1) = 2<sup>[log<sub>2</sub>(*n*)]+1</sup> – 1.
    - Now, 2<sup>[log<sub>2</sub>(*n*)]+1</sup> – 1 is within a constant factor (at most 2) of 2<sup>log<sub>2</sub>(*n*)</sup> = *n*.
    - So T(*n*) ∈ O(*n*), and this is sharp (i.e. T(*n*) and *n* have the same the order of growth in *n*: linear).
