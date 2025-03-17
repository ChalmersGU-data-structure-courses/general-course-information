# Exercises: Complexity, parts B–C

**Note:**
The exercises are optional, but highly recommended.
If you are uncertain about any problem or want to discuss, write in the course discussion channel, or ask a teacher.

The complexity exercises are divided into two parts, one early in the course and a second part later on.
These **B+C** complexity exercises consist of both *core* and *bonus* exercises. We recommend that you try all the core exercises.
Try some of the bonus exercises if you want to learn more.

*Note*: First solve all the early **A** complexity exercises before you try the ones here.

## Core exercises (part B)

**B1**.
Simplify the following orders of growth.

- $O(10 n^10 + 5 n^5 + 2 ^2 + 1)$
- $O(1/n^2 + 1/n + 1)$
- $O((5n + 2)(7 – 3/n)(n + 1))$
- $O(log(n^2) / log(n))$
- $O(log(n^2 + 1) / log(n))$
- $O(1 + n^100 / 2^n)$
- $O(log(log(n)) + log(n))$

**B2**.
Suppose we want to be able to delete elements from a dynamic array of size *n*.

- If we want to delete an arbitrary element, what is the asymptotic complexity in *n*?
- What if deletion is allowed to change the order of the elements in the array?

**B3**.
Give proofs of the following rules for O-notation from the lecture:

- If *f*(*n*) ∈ O(*f*'(*n*)) and *g*(*n*) ∈ O(*g*'(*n*)), then *f*(*n*) *g*(*n*) ∈ O(*f*'(*n*) *g*'(*n*)).
- If *f*(*n*) ∈ O(*f*'(*n*)) and *g*(*n*) ∈ O(*g*'(*n*)), then *f*(*n*) + *g*(*n*) ∈ O(*f*'(*n*) + *g*'(*n*)).
- If *f*(*n*) ∈ O(*f*'(*n*)) and *g*(*n*) ∈ O(*g*'(*n*)), then *f*(*n*) + *g*(*n*) ∈ O(max(*f*'(*n*), *g*'(*n*)).

**B4**.
What are the asymptotic (time) complexities of the following recursive functions?

First write down the mathematical function T(*n*) that the procedure computes (i.e. how many times the statement `sum+=1` is executed).
Since these are recursive functions, you should write a recurrence relation for T(*n*) which may use O-notation.
You can then write down the order of growth of each function.

- **g1**:

  ```
  g1(n):
      if n > 0:
          return 1 + g1(n-1)
      else
          return 0
  ```

- **g2**:

  ```
  g2(n):
      sum = 0
      for i = 1 to n:
          sum += 1
      if n > 0:
          sum += g2(n-1)
      return sum
  ```

- **g3**:

  ```
  g3(n):
      if n > 1:
          return 1 + g3(n/2)
      else:
          return 0
  ```

- **g4**:

  ```
  g4(n):
      sum = 0
      for i = 1 to n:
          sum += 1
      if n > 1:
          sum += g4(n/2)
      return sum
  ```

- **g5**:

  ```
  g5(n):
      if n == 0:
          return 1
      else:
          return g5(n-1) + g5(n-1)
  ```

- **g6**:

  ```
  g6(n):
      int sum = 0
      for i = 1 to n:
          sum += 1
      if n > 1:
          sum += g6(n/2) + g6(n/2)
      return sum
  ```

## Bonus exercises (part C)

**C1** (not really a problem).
Read through some of the stories at [Accidentally Quadratic](https://accidentallyquadratic.tumblr.com) and think about why the asymptotic complexity is quadratic.

**C2**.
Try some of the problems from chapter 1.4 in S&W, such as these ones.
They can all be found ([here, but you have to scroll down a bit](https://algs4.cs.princeton.edu/14analysis/>)).

- *Exercises*: 6
- *Creative Problems*: 14, 18, 19, 20, 34
- *Web Exercises*: 2, 5, 6, 11, 12, 13

**C3**.
Prove or disprove the following statements:

- If $f(n) \in O(g(n))$, then $2^{f(n)} \in O(2^{g(n)}$.
- If $f(n) \in O(g(n))$, then $\log(f(n)) \in O(\log(g(n))$.
  Assume *g*(*n*) ≥ 2 here.

**C4**.
For $f, g \colon \mathbb{N} \to \mathbb{R}_0$, we consider *f* *less or equal than* *g* if *f*(*n*) ∈ O(*g*(*n*)).
Convince yourself that this defines a [preorder](https://en.wikipedia.org/wiki/Preorder) on functions from natural numbers to positive reals.
This means the following:

- Reflexivity: *f*(*n*) = O(*f*(*n*)) (for any *f*).
- Transitivity: if *f*(*n*) = O(*g*(*n*)) and *g*(*n*) = O(h(*n*)), then *f*(*n*) = O(h(*n*)).

Conclude that *f*(*n*) ∈ O(*g*(*n*)) is equivalent to O(*f*(*n*)) ⊆ O(*g*(*n*)),
so the preorder is equivalently that of subset inclusion.

Show that the above preorder is not a total order (so orders of growth, and also complexity classes, are not ordered linearly!).
That is, there are $f, g \colon \mathbb{N} \to \mathbb{R}_0$ such that neither *f*(*n*) ∈ O(*g*(*n*)) nor *g*(*n*) ∈ O(*f*(*n*)).
Show that this holds even when restricted to monotone (increasing) functions.

**C5**.
Let $f \colon \mathbb{N} \to \mathbb{R}_0$ be monotone (increasing).
We say that *f* has *polynomial order of growth* if there is *k* ∈ ℕ such that $f(n) \in O(n^k)$.
Show that *f* has polynomial order of growth if $f(2^n) \in O(f(n))$.
