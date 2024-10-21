# Exercises: Complexity, part A

**Note:** The exercises are optional, but highly recommended. If you are uncertain about any problem or want to discuss, write in the course discussion channel, or ask a teacher.

The complexity exercises are divided into two parts, one early in the course and a second part later on. These early **A** complexity exercises are only ***core*** exercises, and we recommend that you try all of them. The second part will come later in the course.

## Core exercises (part A)

You can try these exercises in connection with the first complexity lecture.

**A1**. What is the asymptotic time complexity (in *n*) of the following operations, assuming that they are implemented efficiently?

1. Finding an element in an unsorted array of *n* elements.
2. Finding an element in a sorted array of *n* elements.
3. Adding an element to an unsorted array of *n* elements, assuming there is an empty space at the end of the array.
4. Adding an element to a sorted array of *n* elements, assuming there is an empty space at the end of the array (the resulting array should also be sorted).

The moral is that all data structures make tradeoffs – choosing a different representation will make some operations faster but others slower.

**A2**. What are the orders of growth of these functions?

- 3*n*<sup>3</sup> + 2*n*<sup>2</sup> + 199
- 3*n*<sup>3</sup> – 2*n*<sup>2</sup> – 199
- 3*n*<sup>3</sup> · 2*n*<sup>2</sup> · 199
- 3*n*<sup>3</sup> / 2*n*<sup>2</sup> / 199
- (*n* + 2*n*<sup>2</sup>)(2*n* + 3*n*<sup>2</sup>)
- (*n* + 2*n*)(2 log<sub>2</sub> *n* + 3 log<sub>2</sub> *n*)

**A3**. Calculate the asymptotic complexities of the following code fragments. Although they are toy examples, the techniques you use are just the same as for realistic programs. Each procedure has been written so that its asymptotic complexity is the same as the order of growth of the mathematical function it computes (why is that?).

First write down the mathematical function T(*n*) that the procedure computes (i.e. how many times the statement `sum+=1` is executed). Fragment **f2** is solved for you already.

- **f1**:

    ```
    sum = 0
    for i = 1 to n:
        sum += 1
    ```

- **f2**:

    ```
    sum = 0
    for i = 1 to n:
        for j = 1 to n-1:
            sum += 1
    ```

  *Answer*:

    - Outer loop runs *n* times
    - For each value of *i*, inner loop runs *n*–1 times.
    - In total, the innermost loop body runs *n*(*n*–1) times.
    - We have T(*n*) = *n*(*n*–1) ∈ O(*n*<sup>2</sup>).

- **f3**:

    ```
    sum = 0
    for i = 1 to n:
        for j = 1 to i:
            sum += 1
    ```

- **f4**:

    ```
    sum = 0
    for i = 0, 2, 4, ..., n/2:
        for j = 0, 3, 6, 9, ..., n/3:
            for k = 0, 5, 10, 15, ..., n/5:
                sum += 1
    ```

- **f5**:

    ```
    sum = 0
    for i = 1 to n:
        sum += 1
    for j = 0 to n:
        sum += 1
    ```

- **f6**:

    ```
    sum = 0
    for i = 1 to n:
        for j = 1 to i:
            sum += 1
    for k = 1 to n:
        sum += 1
    ```

**A4**. Consider an array of n integers. What are the worst-case and average-case asymptotic complexities of sorting the array using:

- insertion sort,
- merge sort,
- quicksort?

Parts of this question are answered by the lectures on sorting. For other parts, you may find the answer in the course book.

**A5**. Suppose you have an array of *n* elements, then you can check if it has duplicate elements in O(*n*<sup>2</sup>) time by looping over every pair of elements. But if the array is sorted, you can do it in O(*n*) time. How?

**A6** (exercise 1.4.12 from S&W). Write a program that, given two sorted arrays of *n* integer values, prints all elements that appear in both arrays, in sorted order. The running time of your program should be proportional to *n* in the worst case.

This program is very similar to a step in one of the algorithms that you have seen in the lectures, but with an small but important difference.

- What is this program similar to?
- What is the difference?

**A7**. This question is about adding an operation to dynamic arrays that deletes the last element of the array.

1. The last element of a dynamic array can be deleted in O(1) time. How?
2. Suppose that we do not try to resize the underlying array when deleting the last element. Then the dynamic array can end up with unlimited overhead – for example, we can end up with an array of capacity 1024 but only one element stored in it. How?
3. To solve this problem, we might decide on the following rule: if the array ever becomes half-empty, resize it to half its current size. Unfortunately, this ruins the efficiency of the design: the time complexity of performing *n* operations (adds and deletes) starting with an empty dynamic array is O(*n*<sup>2</sup>) in the worst case. Find a sequence of operations that demonstrates this.
4. (*Harder*) Tweak the rule in part (3) so that the O(*n*) runtime is preserved. Persuade yourself that your design works.
5. (*Much harder, extremely optional*) Learn about the [potential method](https://en.wikipedia.org/wiki/Potential_method) (not covered in this course, unless we have spare time later) and use it to prove that your design has amortized complexity O(1).

**A8**. Calculate the asymptotic complexities of the following code fragments, just as you did in **A3** above.

- **f7**:

    ```
    sum = 0
    i = 1
    while i ≤ n:
        for j = 1 to n:
            sum += 1
        i *= 2
    ```

- **f8**:

    ```
    sum = 0
    i = 1
    while i ≤ n:
        for j = 1 to n*n:
            sum += 1
        i *= 2
    ```

- **f9**: (This one is trickier than it seems)

    ```
    sum = 0
    i = 1
    while i ≤ n:
        for j = 1 to i:
            sum += 1
        i *= 2
    ```

   *Note*: The only difference between **f7** and **f9** are that in **f7** the inner loop goes to *n*, while in **f9** the inner loop goes to *i*. This makes a difference!

