# Exercise solutions: Hash tables

Here are suggested solutions to the exercises about hash tables.

## Core exercises

### A1. Advantages and disadvantages of hash tables.

The main advantange with hash tables is that the main operations are all constant time, O(1).
BST operations on the other hand are linear, O(n), in the worst case.
However, self-balancing BSTs are logarithmic, O(log n) in the worst case, which is *almost* constant time.

There are two main disadvantages with hash tables:
- They require that the hash function is good, and it is very difficult to create good hash functions in the general case.
  Because if that, hash tables can be exploited by hackers, if we are not very careful when designing the hash functions.
- They are also not *ordered*, meaning that you cannot implement efficient operations for fuzzy searching or finding elements within a range.

### A2. Suitable invariants.

There are many possible, but here are suggestions (where *h(e)* is the table index that the hash function points element *e* to):

- **Separate chaining**: "for every element *e* in the linked list in table cell *k*, *h(e) = k*; also no element in the list occurs twice."

- **Linear probing**: "for every element *e* in table cell *k*, either (1) *h(e) = k*, or (2) *h(e) < k* and all cells *k ≤ i < h(e)* are occupied, or (3) *k < h(e)* and all cells *i ≥ h(e)* and all cells *i < k* are occupied."

### A3. Construct an example to show that deletion is tricky.

Recall the lecture on open addressing hash tables.

### A4. Implement lazy deletion.

Left as exercise, or see the code in the course book.

### A5. Early versions of PHP.

See [this PHP discussion](http://news.php.net/php.internals/70691).

### A6. Is it legal?

Yes, but it would cause all keys to hash to the same spot, which would lead to poor performance.
We discuss good and bad hash functions in the lectures and the lecture videos.

### A7. Implement hashCode and equals for points

See the [S&W website](https://algs4.cs.princeton.edu/34hash/), exercise 2.

The given solution could be generalized to three or more dimensions by dividing the 32 bits of each coordinate into three or more parts and mixing them as before.
For example, for coordinates x<sub>1</sub>, ..., x<sub>n</sub>, we can take **xor** over i = 1, ..., n of x<sub>i</sub> left rotated by ⌊32 / i⌋.

### A8–A10. Insert E A S Y Q U T I O N.

It's not the answer itself that is important, but the practice.
So these are left as exercises for you, but the following table is probably useful – it shows the hash value for each letter, for different values of **m**.
I assume that **A** is the 1<sup>st</sup> letter (not the 0<sup>th</sup>).

<style type="text/CSS"> .mytbl {border-collapse: collapse} .mytbl td, .mytbl th {border: 1px solid black; padding: 2px 10px; text-align: center} </style>
<table class="mytbl">
<tr><th></th><th>A</th><th>E</th><th>I</th><th>N</th><th>O</th><th>Q</th><th>S</th><th>T</th><th>U</th><th>Y</th></tr>
<tr><th>i</th><td>1</td><td>5</td><td>9</td><td>14</td><td>15</td><td>17</td><td>19</td><td>20</td><td>21</td><td>25</td></tr>
<tr><th>m = 5</th><td>1</td><td>0</td><td>4</td><td>4</td><td>0</td><td>2</td><td>4</td><td>0</td><td>1</td><td>0</td></tr>
<tr><th>m = 16</th><td>11</td><td>7</td><td>3</td><td>10</td><td>5</td><td>11</td><td>1</td><td>12</td><td>7</td><td>3</td></tr>
<tr><th>m = 10</th><td>1</td><td>5</td><td>9</td><td>4</td><td>5</td><td>7</td><td>9</td><td>0</td><td>1</td><td>5</td></tr>
<tr><th>m = 4</th><td>3</td><td>3</td><td>3</td><td>2</td><td>1</td><td>3</td><td>1</td><td>0</td><td>3</td><td>3</td></tr>
<tr><th>m = 8</th><td>3</td><td>7</td><td>3</td><td>2</td><td>5</td><td>3</td><td>1</td><td>4</td><td>7</td><td>3</td></tr>
</table>


## Bonus exercises

Most of the following bonus exercises are from the Sedgewick & Wayne book.
Some of them can be found at the [book website](https://algs4.cs.princeton.edu/34hash/).

### B1. Birthday paradox

See the [S&W website](https://algs4.cs.princeton.edu/34hash/), exercise 8.

With replacement means that the same song can be chosen more than once. Each time we play a new song we will have increased the number of songs that are likely to be a duplicate.

[Here](https://betterexplained.com/articles/understanding-the-birthday-paradox/) you can read about the birthday paradox.

### B2 Insert E A S Y Q U T I O N.

See the answer to A8–A10 above.

### B3. Hash attack

See the [S&W website](https://algs4.cs.princeton.edu/34hash/), exercise 32.

It is easy to verify that "Aa" and "BB" hash to the same hashCode() value (2112).
Now, any string of length 2N that is formed by concatenating these two strings together in any order (e.g., BBBBBB, AaAaAa, BBAaBB, AaBBBB) will hash to the same value.
Here is a list of [10000 strings with the same hash value](https://algs4.cs.princeton.edu/34hash/hash-attack.txt).

### B4. Bad hash functions

See the [S&W website](https://algs4.cs.princeton.edu/34hash/), exercise 33.

This was done in the hopes of computing the hash function more quickly.
Indeed, the hash values were computed more quickly, but it became more likely that many strings hashed to the same values.
This resulted in a significant degradation in performance on many real-world inputs (e.g., long URLs) which all hashed to the same value, e.g., `http://www.cs.princeton.edu/algs4/34hash/*****java.html`.

### B5. Avoiding lazy deletion

One example of where it goes wrong:
Let's say we have an empty hash table and three objects we want to insert "hearts", "diamonds" and "clubs. "Diamonds" and "clubs" have the same hash value and "hearts" hash value is "diamonds -1".

- We first insert "hearts" in the empty table, no collision.
- We then insert "diamonds" in the table now only containing hearts, no collision but these two now build a cluster.
- We finally insert "clubs" in the table, it will collide with "diamonds" so we probe 1 ahead.
  Our cluster now contains 3 objects.
- Now we remove "hearts".
  According to the rule we should find the last element of the cluster, which is "clubs", and swap them to keep the cluster intact.

The problem now is that when we go looking for clubs, it will be positioned _before_ where we start looking.

See Sedgewick & Wayne, page 471, or the [Wikipedia article about linear probing](https://en.wikipedia.org/wiki/Linear_probing#Deletion).

### B6. Insert A–G in some order.

Write a program that tries to insert the keys in all possible orders.
From the results you can fill in this table:

<table class="mytbl">
<tr><th></th><th>Possible?</th><th>Minimal probes</th><th>Maximal probes</th></tr>
<tr><th>1. E F G A C B D</th><td></td><td></td><td></td></tr>
<tr><th>2. C E B G F D A</th><td></td><td></td><td></td></tr>
<tr><th>3. B D F A C E G</th><td></td><td></td><td></td></tr>
<tr><th>4. C G B A D E F</th><td></td><td></td><td></td></tr>
<tr><th>5. F G B D A C E</th><td></td><td></td><td></td></tr>
<tr><th>6. G E C A D B F</th><td></td><td></td><td></td></tr>
</table>

### B7. (S&W exercise 3.4.4).

Left as an exercise.
