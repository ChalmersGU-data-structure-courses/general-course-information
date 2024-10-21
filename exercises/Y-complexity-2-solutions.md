# Exercise solutions: Complexity, parts B–C

Here are suggested solutions to the exercises about complexity, parts B and C.

## Core exercises (part B)

### B1. Simplify orders of growth

- O(10n<sup>10</sup> + 5n<sup>5</sup> + 2n<sup>2</sup> + 1) = O(n<sup>10</sup>) (constant factors don't matter, only the largest summand matters).
- O(1/n<sup>2</sup> + 1/n + 1) = O(1) (only the largest summand matters).
- O((5n + 2)(7 - 3/n)(n + 1)) = O(n ∙ 1 ∙ n) = O(n<sup>2</sup>) (taking orders of growth preserves products, see B3).
- O(log n<sup>2</sup> / log n) = O(1) since log(n<sup>2</sup>) / log n = 2 log n / log n = 2.
- O(log (n<sup>2</sup> + 1) / log n) = O(1) by the previous item and log (n<sup>2</sup> + 1) ≤ log (2n<sup>2</sup>) = log 2 + 2 log n = O(log n).
- O(1 + n<sup>100</sup> / 2<sup>n</sup>) = O(1). This is because n<sup>a</sup> ≤ b<sup>n</sup> for large enough n, so long as a > 1 and b > 1.
- O(log (log n) + log n) = O(log n). To see this, note that log x < x for large enough x, so log (log n)) ∈ O(log n).

### B2. Deletion from a dynamic array

(We assume that the dynamic array does not resize automatically after deletion, which is in fact how ArrayList behaves in Java.)

- The complexity of deleting an arbitrary element is linear in the number of elements n: In the worst case, this element is the first, and then we have to move all other elements one step forward, which takes O(n) time.
- If we are allowed to change the order, we can implement deletion as a constant time operation (O(1)): we just move the last element to the position of the removed element.

### B3. Give proofs of the following rules for O-notation

All cases have the same hypotheses. These give us:

- C, m<sub>0</sub> such that f(n) ≤ C f'(n) for n ≥ m<sub>0</sub>,
- D, n<sub>0</sub> such that g(n) ≤ D g'(n) for n ≥ n<sub>0</sub>.

Then we have:

- f(n) g(n) ≤ (C f'(n)) (D g'(n)) = (C D) f'(n) g'(n) for n ≥ max(m<sub>0</sub>, n<sub>0</sub>), so f(n) g(n) ∈ O(f'(n) g'(n)).
- f(n) + g(n) ≤ C f'(n) + D g'(n) ≤ max(C, D) (f'(n) + g'(n)) for n ≥ max(m<sub>0</sub>, n<sub>0</sub>), so f(n) + g(n) ∈ O(f'(n) + g'(n)).
- We have f'(n) + g'(n) ≤ 2 max(f'(n), g'(n)) ∈ O(max(f'(n), g'(n)). The claim follows from the previous item and this by transitivity of the complexity ordering.

### B4. Asymptotic complexities of recursive functions

- **g1**. By induction, we see that T(n) = n, so T(n) ∈ O(n) (linear complexity). The example is a recursive presentation of **f1** above.

- **g2**. We have T(0) = 0 and T(n + 1) = T(n) + n. An exact solution is T(n) = n(n+1)/2 (proved by induction), so T(n) ∈ O(n<sup>2</sub>) (quadratic complexity). Alternatively, one can reason T(n) = 1 + 2 + … + n ≤ n ∙ n = n<sup>2</sub> ∈ O(n<sup>2</sub>). This is sharp because T(n) = 1 + 2 + … + n ≥ ⌈(n+1)/2⌉ + … + n ≥ n/2 ∙ n/2 = 1/4 n<sup>2</sub>.

    - *Note*. This is a useful strategy for all sorts of sums of increasing terms: a simple upper bound can be obtained by bounding each summand by the largest one. A simple lower bound can be obtained by throwing away the smallest half and bounding each remaining summand by the smallest one. If these bounds differ only by a constant factor, this is the complexity of the sum.

- **g3**. This is the skeleton of binary search. The function computes T(n) = ⌊log<sub>2</sub>(n)⌋ (how many times do we have divide n by 2 until the result is less than 2?). Thus, T(n) ∈ O(log n) (logarithmic complexity).

- **g4**. This is the skeleton of [quick select](https://en.wikipedia.org/wiki/Quickselect). We have T(1) = 1 and T(n) = n + T(n/2) for n > 1. For n = 2<sup>m</sub>, we have T(2<sup>m</sub>) = 2<sup>m</sub> + T(2<sup>m–1</sub>) = 2<sup>m</sub> + 2<sup>m–1</sub> + T(2<sup>m–2</sub>) = … = 2<sup>m</sub> + … + 2 + 1 + T(1) = 2<sup>m+</sub> (by induction or the formula for geometric sums), that is, T(n) = n. For the general case, let n' be the largest power of 2 bounded by n. T is increasing, so we have T(n') ≤ T(n) ≤ T(2n'), so n/2 ≤ T(n) ≤ 2n, which gives T(n) ∈ O(n) (linear complexity) strictly.

- **g5**. We have T(0) = 1 and T(n + 1) = 2 T(n), so by induction we have T(n) = 2<sup>n</sub> ∈ O(2<sup>n</sub>) (exponential complexity with base 2).

- **g6**. This is the skeleton of merge sort. We have T(1) = 1 and T(n) = n + 2 T(n/2) for n > 1. For n = 2<sup>m</sub>, we have T(2<sup>m</sub>) = 2<sup>m</sub> + 2T(2<sup>m–1</sub>) = 2<sup>m</sub> + 2<sup>m</sub> + 4T(2<sup>m–2</sub>) = … = 2<sup>m</sub> + … + 2<sup>m</sub> + 2<sup>m</sub> T(1) = 2<sup>m</sub> ∙ (m + 1), that is, T(n) = n (log<sub>2</sub> n + 1). For the general case, let n' be the largest power of 2 bounded by n. T is increasing, so we have T(n') ≤ T(n) ≤ T(2n'), so n/2 (log<sub>2</sub> n/2 + 1) ≤ T(n) ≤ 2n (log<sub>2</sub> 2n + 1), which is n/2 log<sub>2</sub>(n) ≤ T(n) ≤ 2n (log<sub>2</sub> n + 2), which gives T(n) ∈ O(n log n) strictly.


## Bonus exercises (part C)

### C1. Accidentally Quadratic

There's no answer, since this wasn't really a question…

### C2. Problems from S&W chapter 1.4

Some of the problems have answers or hints on the website, otherwise you're on your own:)

### C3. Prove or disprove

- The first statement is false. To see this, put f(n) = 2n and g(n) = n. We have 2n ∈ O(n), but not 2<sup>2n</sup> ∈ O(2<sup>n</sup>). Indeed, if 2<sup>2n</sup> ∈ O(2<sup>n</sup>) were to hold, there would be C such that 2<sup>2n</sup> ≤ C 2<sup>n</sup> for large enough n. But since 2<sup>2n</sup> = 2<sup>n</sup>·2<sup>n</sup>, that would mean 2<sup>n</sup>·2<sup>n</sup> ≤ C·2<sup>n</sup> for large enough n. And if we divide by 2<sup>n</sup> on both sides, we get 2<sup>n</sup> ≤ C for large enough n, which is a falsehood since 2<sup>n</sup> grows arbitrarily large.

- The second statement is true. We are given C and n<sub>0</sub> such that f(n) ≤ C g(n) for n ≥ n<sub>0</sub>. Since log is monotone, we have log f(n) ≤ log (C g(n)) = log C + log g(n) ≤ (D + 1) log g(n) for n ≥ n<sub>0</sub> where D is chosen so that log(C) ≤ D log g(n): if log C ≤ 0, we take D = 0, otherwise, we take D = log C / log 2 using that g(n) ≥ 2. Thus, log f(n) ∈ O(log g(n)).

### C4. Preorder

Reflexivity (f(n) ∈ O(n)) holds trivially: we have f(n) ≤ 1 ∙ f(n) for n ≥ 1. For transitivity, if f(n) is bounded by C g(n) for n ≥ n0 and g(n) is bounded by D h(n) for n ≥ n1, then f(n) is bounded by CD h(n) for n ≥ max(n0, n1). Thus, the relation defined by O forms a preorder (called the order-of-growth order).

If O(f(n)) ⊆ O(g(n)), then f(n) ∈ O(g(n)) follows from reflexivity (f(n) ∈ O(n)). Conversely, if f(n) ∈ O(g(n)), then O(f(n)) ⊆ O(g(n)) follows using transitivity established above.

Let us construct f, g : ℕ → ℝ>0 such that neither f(n) ∈ O(g(n)) nor g(n) ∈ O(f(n)). There are many possible ideas, one is the following:

f(n) = n and g(n) = 1 for n even,
f(n) = 1 and f(n) = n for n odd.
The ratio f(n) / g(n) grows arbitrarily large. Thus, there cannot be C and n₀ such that f(n) / g(n) ≤ C for n ≥ n₀. This shows that f(n) ∈ O(g(n)) does not hold. An analogous argument shows that g(n) ∈ O(f(n)) does not hold.

From this example, we can build another one whose functions are increasing. The idea is to multiply f and g by the same fast-growing function h, i.e. set f'(n) = h(n) f(n) and g'(n) = h(n) g(n). Then the ratios of f' and g' are identical to those of f and g, so neither f'(n) ∈ O(g'(n)) nor g'(n) ∈ O(f'(n)) hold. Picking the factorial function h(n) = n! makes f' and g' increasing.

### C5. Polynomial order of growth

Assume f(2n) ∈ O(f(n)). That means there are C and n<sub>0</sub> such that f(2n) ≤ C f(n) for n ≥ n<sub>0</sub>. By induction on m, we get that f(2<sup>m</sup>) ≤ C<sup>m</sup> f(1). Since f is increasing, we have

- f(n) ≤ f(2<sup>⌈log<sub>2</sub> n⌉</sup>) ≤ C<sup>⌈log<sub>2</sub> n⌉</sup> f(1) = O(C<sup>log<sub>2</sub> n</sup>) = O(n<sup>log<sub>2</sub> C</sup>)

So f ∈ O(n<sup>k</sub>) for k = log<sub>2</sub>(C).

