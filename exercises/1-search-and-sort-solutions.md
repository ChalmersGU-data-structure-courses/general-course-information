# Exercise solutions: Search and sort

Here are suggested solutions to some of week 1's exercises.

## Core exercises

### A1. Adapt binary search so that it works on arrays that are sorted in descending order.

Suppose we are searching for 5 in the array `[9, 7, 5, 4, 3, 2, 1]`.
We first search the midpoint, which is 4.
Since the array is in descending order, 5 should come *before* 4, so we should search in the *left* half of the array.
So the procedure we use follows the *opposite* rules compared to binary search:

- If the item we are searching for is *less* than the midpoint, search in the *right* half of the array.
- If the item we are searching for is *greater* than the midpoint, search in the *left* half of the array.

Here it is in pseudocode.
It's just like the normal binary search algorithm, except that the two lines marked `(*)` have been swapped.

```python
binarySearch(array, item):
    lo = 0
    hi = array.length() - 1
    while lo <= hi:
        # we use integer division here, rounding down to the nearest integer:
        mid = (lo + hi) // 2
        if item < array[mid]:
            # item must be in second half of array
(*)         lo = mid+1
        else if item > array[mid]:
            # item must be in first half of array
(*)         hi = mid-1
        else:
            # we found the item
            return mid
    # item not found
    return -1
```

### A2. Finding the integer square root.

We use the same principles as binary search: make a guess, and then figure out if the guess was *too high*, *too low* or *correct*.
Suppose that we guess *m* as the square root of *n*. Then we can check our guess as follows:

- If *m*<sup>2</sup> ≤ *n* < (*m*+1)<sup>2</sup>, then the guess is *correct*.
- If *m*<sup>2</sup> > *n*, then the guess is *too high*.
- Otherwise, the guess is *too low*.

We also need a lower and upper bound on the correct value of *m*.
Since the integer square root of *n* always lies between 0 and *n*, we can use those as the initial bounds.
We get the following psuedocode:

```python
integerSquareRoot(n):
    lo = 0
    hi = n
    while true:
        int m = (lo + hi) // 2
        if m * m > n:
            # we guessed too high, restrict search to below m
            hi = m - 1
        else if (m+1) * (m+1) <= n:
            # we guessed too low, restrict search to above m
            lo = m + 1
        else: # m*m <= n and (m+1)*(m+1) > n
            # we guessed right
            return m
```

**Note**:
How do computers actually compute the square root?
They also start with a guess and continue to improve it.
The [simplest practical method](https://en.wikipedia.org/wiki/Methods_of_computing_square_roots#Babylonian_method) is as follows:
Suppose the current guess is called *x*.
If *x* is smaller than *√n*, then *n/x* is larger than *√n*, and vice versa.
So we take their average for the next guess!

### A3. Sorting {4,6,8,2,9,5,1} by hand

#### Insertion sort

The symbol `|` indicates the boundary between the sorted and unsorted parts of the array.

```
4 | 6 8 2 9 5 1 - now insert 6
4 6 | 8 2 9 5 1 - now insert 8
4 6 8 | 2 9 5 1 - now insert 2
2 4 6 8 | 9 5 1 - now insert 9
2 4 6 8 9 | 5 1 - now insert 5
2 4 5 6 8 9 | 1 - now insert 1
1 2 4 5 6 8 9
```

#### Quicksort, using median-of-three

`^` indicates the three options for pivot element in median-of-three.

First, partition the array:

```
4 6 8 2 9 5 1 - pivot is 2, swap with 4
^     ^     ^

2 6 8 4 9 5 1 - swap 1 and 6
  lo        hi

2 1 8 4 9 5 6 - lo is stuck, hi moves all the way to the left
    lo    hi

2 1  8 4 9 5 6 - now swap pivot with hi
  hi lo

1 2 8 4 9 5 6 - underlined parts are partitions
-   ---------
```

Next, make two recursive calls to sort the two partitions.
The left partition `{1}` is a base case.
Here is what happens with the right partition `{8,4,9,5,6}` (`|` indicates the part of the array we are sorting):

```
1 2 | 8 4 9 5 6 - pivot is 8
      ^   ^   ^

1 2 | 8 4 9 5 6 - move lo right
        lo    hi

1 2 | 8 4 9 5 6 - swap lo and hi
          lo  hi

1 2 | 8 4 6 5 9 - lo moves right one step
            lo
            hi

1 2 | 8 4 6 5  9 - now swap 5 with pivot
            hi lo

1 2 | 5 4 6 8 9
      -----   -
```

Finally, we make two recursive calls, one to sort `{5,4,6}` and one to sort `{9}`.

### A4. Implement some functions used in sorting algorithms

```python
minimum(array):
    minimumSoFar = array[0]
    for i in 1 to array.length()-1:
        if array[i] < minimumSoFar:
            minimumSoFar = array[i]
    return minimumSoFar
```

```python
insert(array, x):
    # First find the insertion point.
    # Loop through the array but skipping the blank last element.
    for i in 0 to array.length()-2:
        if array[i] > x:
            # The insertion point is here!
            # Copy everything up one place. Here is one way to do it.
            for j in array.length()-2 down to i:
                array[j+1] = array[j]
            # Now insert the value
            array[i] = x
            return
    # x is the greatest item in the array
    array[array.length()-1] = x
```

```python
merge(array1, array2):
    result = new array of size array1.length()+array2.length()
    i = 0  # index in array1
    j = 0  # index in array2
    k = 0  # index in result

    # Merge until one array is done
    while i < array1.length() and j < array2.length():
        if array1[i] <= array2[j]:
            result[k] = array1[i]
            i += 1
        else:
            result[k] = array2[j]
            j += 1
        k += 1

    # Copy the remaining data from whichever array is not done
    while i < array1.length:
        result[k] = array1[i]
        i += 1
        k += 1
    while j < array2.length:
        result[k] = array2[j]
        j += 1
        k += 1

    return result
```

## Bonus exercises

### B1. Use binary search to make a "guess-the-number" game.

The code is like normal binary search, but instead of using the Java comparison functions, ask a question to the user.

You can, e.g., use two numbers MIN and MAX, which start at MIN = 0 and MAX = 10,000.
Then repeat guessing the average number, and update MIN or MAX depending on my answer.
The code is similar to integer square root.

### B1 (HARDER). Extend your program so that I can pick any positive number.

First we have to find a MAX which is larger than the number I am thinking about.
We can do this by repeated doubling: Start by guessing (say) 10,000.
If my number is larger, then double your guess until you exceed my number.
Now you can set MAX to the last guess and continue using binary search.

Why double the guess every time?
Because that way, if I am thinking of some large number n, the program guesses the value of MAX in *log_2_ n* guesses, and then starts the binary search.
So, this way it can guess the exact number in a logarithmic number of guesses, regardless of how large a number I am thinking of.

### B2. Removing all duplicates; finding the mode

Both these exercises are a bit tricky!

#### Removing all duplicates.

First we sort the array so that duplicate elements come next to each other.
Then we are going to create an output array containing the input array without duplicates.
To do so, we first count how many duplicates there are, create an output array of that size and then copy the input to the output while skipping duplicates.

**Note:**
Counting the number of duplicates is only needed if we want to store the result in an array, because then we need to know the capacity of the array up-front.
If we are storing the result in e.g. a dynamic array then we can skip that step!

```python
# The code below only works for non-empty arrays
if array.length() == 0: return array

sort the array

# Count how many duplicates there are.
# This step can be skipped if we make 'output' (below) a dynamic array!
count = 1
for i in 1 to array.length()-1:
    if array[i] != array[i-1]:
        count += 1

output = new array of size count
output[0] = array[0]
j = 1
for i in 1 to n:
    if array[i] != array[i-1]:
        output[j] = array[i]
        j += 1
```

#### Finding the most common element.

First we sort the array.
Then we loop through the array, keeping track of:

- the most common element so far,
- how many times that element has occurred,
- the element we are currently looking at,
- how many times that element has occurred.

```python
# First sort the array so that all occurrences of the same value occur next to one another in the array.
sort the array

mostCommonElement = currentElement = null
mostCommonCount = currentCount = 0

for each elem in array:
    # Check if current element has changed
    if elem != currentElement:
        currentElement = elem
        currentCount = 1
    else:
        currentCount += 1

    # Check if this element is now the most common
    if currentCount > mostCommonCount:
        mostCommonElement = currentElement
        mostCommonCount = currentCount

return mostCommonElement
```

### B5. Finding anagrams

#### a) How can you use sorting to check if two words are anagrams of one another?

Sort the letters in each word in ascending order.
If the words are anagrams, sorting them should give the same string.
For example, "silent" is an anagram of "listen" because sorting the letters of either of them gives "eilnst".

#### b) Write a program that reads in a list of words and efficiently finds all anagrams.

Define a function `anagramForm(word)` which returns the letters of the given `word` in alphabetical order.
For example, `anagramForm("listen") == "eilnst"`.

Now sort the words, but using a custom ordering: instead of sorting the words in alphabetical order, sort them according to the alphabetical order of their anagram form.
In Java, this can be done using

```java
words.sort(Comparator.comparing(word -> anagramForm(word)));
```

and in Python using

```python
words.sort(key = lambda word: anagramForm(word))
```

Now you have a list of all words, ordered by their anagram form.
Then given a word, you can compute its anagram form, and use binary search on this list to find all words having the same anagram form.
Note that you need the specialised binary searches from lab 2 to find the first and last match in the list.

## Extreme exercises

We won't spoil these.
You can continue to try them over the course!
