# Exercises: Search and sort

**Note:**
The exercises are optional, but highly recommended.
If you are uncertain about any problem or want to discuss, write in the course discussion channel, or ask a teacher.

The exercises are divided into ***core*** and ***bonus*** (and some ***extreme*** ones).
We recommend you try all the core exercises. Try some of the bonus exercises if you want to learn more.

## Core exercises

**A1**.
Adapt binary search so that it works on arrays that are sorted in *descending* instead of ascending order.

<details><summary><em>Hint:</em></summary>
First write down an example array and try to do the binary search "by hand". Then figure out what rules you followed.
</details>

**A2**.
The *integer square root* of a natural number *n* is the largest natural number *m* such that *m<sup>2</sup> ≤ n*.
For example, the integer square root of 105 is 10.

Design an algorithm to calculate the integer square root of *n* using binary search.
You can use multiplication and comparison of integers.

**A3**.
Sort the sequence `4 6 8 2 9 5 1` by hand with:

- insertion sort,
- quicksort (using the median-of-three pivot),
- mergesort.

**A4**.
Implement (in code or pseudocode) the following methods, which are important components of sorting algorithms:

- `minimum(array)`, which finds the smallest element in an array, and returns the value found.
- `insert(array,x)`, which inserts the value `x` into a *sorted array*.
  You should assume that `array` contains a sorted list of items, followed by an unused space at the end (so that there's room to insert the new item).
- `merge(array1,array2)`, which merges two sorted arrays and returns a new array.


## Bonus exercises

**B1**.
Use binary search to make a "guess-the-number" game: I think of a number between 1 and 10000, your program guesses a number and I reply whether my number is higher or lower.
Your program makes another guess and so on until it gets the right number.

**Harder:** extend your program so that I can pick any positive number, not just ones up to 10000.

<details><summary><em>Hint:</em></summary>
First try to find a number which is bigger than mine.
</details>

**B2**.
Write programs (in code or pseudocode) that use sorting to solve the following problems:

- Given an array, remove all duplicate elements.
- Given an array, find the most common element.

**B3**.
Can you describe what algorithm you use when looking up a word in a (real-life) dictionary?
It probably isn't a binary search – if you are looking for a word starting with A, you probably look near the beginning of the dictionary, whereas binary search always starts in the middle.
Does the algorithm you use change when you get close to the target word?

- After answering this question, you may want to read about [interpolation search](https://en.wikipedia.org/wiki/Interpolation_search).

**B4**.
Suppose that you want to sort the books on your bookshelf, say into alphabetical order, by hand.

- What would be a good algorithm for doing this?
- Does the answer change if you have very many (say thousands) of books?
  Does it depend on what order the books are currently in?
- Think about why a good computerised sorting algorithm may be bad for sorting a bookshelf, and vice versa.
  For example, are there things we can efficiently do to a bookshelf which are harder with an array?
  Are other things than efficiency important?

**B5**.
How can you use sorting to check if two words are anagrams of one another?

<details><summary><em>Hint:</em></summary>
You will need to sort the array in an order which makes all anagrams appear next to each other.
</details>

**Harder:** write a program that reads in a list of words and efficiently finds all anagrams.

## Extreme exercises

In the following problems, you have a sorted list of *n* elements and a key, all different from each other.
Your goal is to find out where in the sorted list the key should be inserted. But you cannot make any comparisons yourself!

**C1**.
Every morning, you can choose an element of the list and ask if it is smaller than the key.
However, you get the answer only on the evening of the following day (after 36 hours).
(Comparisons can take a long time, you know!)
For example, you get the answer to your first question only after you ask the second question.

- If *n* = 250, how many days do you need to find the answer?
- What's the largest *n* for which you can get the answer within 20 days?

**C2**.
You can choose any element of the list and **guess** if it is smaller than the key.
But you can guess wrong at most three times!

- If *n* = 100, how many guesses do you need to find the answer?
- What's the largest *n* for which you can find the answer with 10 guesses?

<details><summary><em>Hint:</em></summary>
First try to solve it with three times replaced by two times (or even just one time).
</details>
