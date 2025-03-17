# Exercises: Hash tables

**Note:**
The exercises are optional, but highly recommended.
If you are uncertain about any problem or want to discuss, write in the course discussion channel, or ask a teacher.

The exercises are divided into ***core*** and ***bonus***.
We recommend you try all the core exercises.
Try some of the bonus exercises if you want to learn more.

## Core exercises

Some of the exercises below are from the Sedgewick & Wayne book.
Some of them can be found at the [website for the book to the Sedwick & Wanye](https://algs4.cs.princeton.edu/34hash/).

**A1**.
What are the advantages and disadvantages of hash tables compared to binary search trees?

**A2**.
Write down a suitable invariant for:

- hash tables with separate chaining,
- hash tables with linear probing.

**A3**.
When using linear probing, deletion is tricky.
Construct an example to show this, i.e., when simply deleting the item gives the wrong result.

**A4**.
One simple way to implement deletion in a linear probing hash table, is to use lazy deletion.
This means that instead of actually deleting the element, we overwrite it with a special value "DELETED".
Implement this.

**A5**.
In early versions of the PHP programming language, the hash function used for strings was the length of the string.
Can you think of any problems this would cause?

------------

The following exercises are from the Sedgewick & Wayne book.
Some of them can be found at the [book website](https://algs4.cs.princeton.edu/34hash/).

**A6** (S&W exercise 5).
Is the following implementation of `hashCode()` legal?

```python
hashCode():
    return 17
```

**A7** (S&W web exercise 2).
Implement `hashCode()` and `equals()` for the following data type.
Assume that most points have small values for x and y (relative to the possible size of an int).
Your hash codes should have good quality under this assumption.

```python
class Point2D:
    x: real number
    y: real number
```

Does your solution generalize to points in three dimensions or more?

**A8** (S&W exercise 3.4.1).
Insert the keys **E A S Y Q U T I O N** in that order into an initially empty hash table of size **m**.
Use the hash function **(11 · k) % m** to transform the kth letter of the alphabet into a table index.

Do this using a separate chaining hash table, and a hash table of **m = 5** lists.

**A9** (S&W exercise 3.4.10a).
Do the same as **A8**, but using linear probing, and a hash table of size **m = 16**.

**A10** (S&W exercise 3.4.10b).
Do the same as **A9**, but using a hash table of size **m = 10**.

## Bonus exercises

Most of the following bonus exercises are from the Sedgewick & Wayne book.
Some of them can be found at the [book website](https://algs4.cs.princeton.edu/34hash/).

**B1** (S&W web exercise 8, *birthday paradox*).
Suppose your music jukebox plays songs from your library of 4000 songs at random (with replacement).
How long do you expect to wait until you hear a song played for the second time?

**B2** (S&W exercise 3.4.11).
Do the same as in questions A9 and A10 above, but using a hash table of initial size **m = 4**, that is expanded with doubling whenever half full.

**B3** (S&W creative exercise 32, *hash attack*).
Find 2<sup>*N*</sup> strings, each of length *N*, that have the same `hashCode()` value, supposing the `hashCode()` implementation for String (as specified in the [Java standard](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/String.html#hashCode())) is the following:

```python
hashCode(string):
    hash = 0
    for each char in string:
        hash = 31 * hash + ascii code of char
    return hash
```

**B3b** (S&W exercise 3.4.32b).
Write a program that showcases the problem in B2:
Insert all 2<sup>*N*</sup> strings, except one, into a hash table.
Then lookup the missing string.
Repeat the lookup a number of times (e.g., 1,000,000 times), and measure how long time it takes.
Then do the same thing with 2<sup>*N*</sup> strings with different hash codes (e.g., by using different seed strings than "Aa" and "BB"). Do this for different n, and draw a graph of the time it takes to lookup one element.

**Note**:
If you're using Python you have to implement the hash function yourself, because Python uses a much better hash function for strings than Java.
Also, you probably need to use the hash table implementation from the course, and not rely on Python's own `dict`.

**B4** (S&W creative exercise 33, *bad hash function*).
Consider the following `hashCode()` implementation for String, which was used in early versions of Java:

```python
hashCode(string):
    hash = 0
    skip = Math.max(1, string.length() / 8)
    for i in 0 ... string.length():
        hash = (hash * 37) + charAt(i);
    return hash
```

Explain why you think the designers chose this implementation and then why you think it was abandoned in favor of the one in the previous exercise.

**B5** (follow-up to question A4).
We might try to avoid lazy deletion as follows.
To delete an element x, we first find the element, then find the last element in that cluster (call it y), and overwrite x with y in the array (and delete y).

The idea is that this keeps the cluster in one piece, thus not breaking the invariant.
However, it doesn’t work. Find an example where it goes wrong.

Can you think of a way to fix this method, without going back to lazy deletion?
It may help to think about the hash table’s invariant.

**B6** (S&W exercise 3.4.12, harder).
Suppose that the keys **A** through **G**, with the hash values given below, are inserted in some order into an initially empty linear probing hash table of size **m = 7**, using no resizing.

<style type="text/CSS"> .mytbl {border-collapse: collapse} .mytbl td, .mytbl th {border: 1px solid black; padding: 2px 10px; text-align: center} </style>
<table class="mytbl">
<tr><th>key</th><td>A</td><td>B</td><td>C</td><td>D</td><td>E</td><td>F</td><td>G</td></tr>
<tr><th>hash</th><td>2</td><td>0</td><td>0</td><td>4</td><td>4</td><td>4</td><td>2</td></tr>
</table>

Which of the following could not possibly result from inserting these keys?

1. **E F G A C B D**
2. **C E B G F D A**
3. **B D F A C E G**
4. **C G B A D E F**
5. **F G B D A C E**
6. **G E C A D B F**

Give the minimum and the maximum number of probes that could be required to build a table of size 7 with these keys, and an insertion order that justifies your answer.

**B7** (S&W exercise 3.4.4, harder).
Write a program to find values of **a** and **m**, with **m** as small as possible, such that the hash function **(a · k) % m** for transforming the **k**<sup>th</sup> letter of the alphabet into a table index produces distinct values (no collisions) for the keys **S E A R C H X M P L**.
The result is known as a *perfect hash function*.


