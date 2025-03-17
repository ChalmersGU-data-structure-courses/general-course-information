# Exercises: Sequences

**Note:**
The exercises are optional, but highly recommended.
If you are uncertain about any problem or want to discuss, write in the course discussion channel, or ask a teacher.

The exercises are divided into ***core*** and ***bonus***.
We recommend you try all the core exercises.
Try some of the bonus exercises if you want to learn more.

## Core exercises

**A1**.
Assume you have a program that reads words from the terminal or from a text file – if there are several words in one line it splits them into a list of words.
Every word is pushed onto a stack, but if the word is "–", the stack is instead popped and the result printed to the terminal.
When there are no more words to read the program print the number of items that are left on the stack, and then quits.

- What is the result of running the program on the following input: `it was - the best - of times - - - it was - the - -`?

**A2**.
The same as question A1, but using a queue instead.

**A3**.
Give an algorithm that removes all comments from a program.
Assume that comments are written as `{ ... }` and can be nested (i.e. `{ a comment with {another comment} inside }`).
Write your algorithm in pseudocode if you like.
What is the complexity of your algorithm?

**Harder:**
Suppose that there are two different kinds of comments: `{ ... }` and `[ ... ]`.
These must be correctly nested, for example `{A [B} C]` is not correct, but `{A [B] C}` is.
Design an algorithm that checks if all comments are correctly nested.

**A4**.
Write a program that takes a [postfix expression](https://en.wikipedia.org/wiki/Reverse_Polish_notation) (as a sequence of strings) and evaluates it to an integer.
Example: The postfix expression `3 7 5 + 2 / *` means `3 * ((7 + 5) / 2)` and should evaluate to 18.
Which ADT is useful here?
(The advantage of postfix expressions is that they don't need any brackets.)

**A5**.
Recall the following question from the quiz, about queues:

> Suppose that a client performs an intermixed sequence of (queue) enqueue and dequeue operations.
> The enqueue operations put the integers 0 through 9 in order onto the queue; the dequeue operations print out the return value.
> Which of the following sequence(s) can never occur?

Try to come up with a rule that tells if a sequence is possible or not.

**A6**.
Design a data structure that represents an array of unlimited size: unlike a normal array, there is no maximum index that can be written to.
It should support the following operations:

- `get(index)`: return the element at a given index; if that element has not yet been set, it should return `null`/`None`.

- `set(index, value)`: modify the element at a given index.

- <details><summary><em>Hint:</em></summary>

  To implement the data structure, use a normal array but automatically grow it when necessary.
  Use the array-doubling trick to ensure good performance.
  </details>

- <details><summary><em>Hint:</em></summary>

  Note that in `set(...)`, if the index is much bigger than the current size of the array, you may have to double the size more than once.
  </details>

## Bonus exercises

**B1**.
Implement the programs described in questions **A1** and **A2**.

**B2**.
The same as question **A5**, but for stacks:

> Suppose that an intermixed sequence of (stack) push and pop operations are performed.
> The pushes push the integers 0 through 9 in order; the pops print out the return value.
> Which of the following sequence(s) can never occur?

Try to come up with a rule that tells if a sequence is possible or not.
Note that this is trickier than for queues.

**B3**.
The following exercises are all from Sedgewick & Wayne.
Note that some of them (but not all) have solutions or hints on the book website.

**Heading "Exercises" on the Sedgewick & Wayne website**: <https://algs4.cs.princeton.edu/13stacks/>

- **4**:
  Write a stack client that reads in sequence of left and right parentheses, braces, and brackets from standard input and uses a stack to determine whether the sequence is properly balanced.
  For example, your program should print **true** for `[()]{}{[()()]()}` and **false** for `[(])`.

- **6**: What does the following code fragment do to the queue `q`?

    ```python
    s = new Stack()
    while q is not empty:
        s.push(q.dequeue())
    while s is not empty:
        q.enqueue(s.pop())
    ```

**Heading "Web Exercises" on the Sedgewick & Wayne website**: <https://algs4.cs.princeton.edu/13stacks/>

- **31**: *Queue with two stacks*.
  Implement a queue with two stacks so that each queue operations takes a constant amortized number of stack operations.
  - <details><summary><em>Hint:</em></summary>
    If you push elements onto a stack and then pop them all, they appear in reverse order.
    If you repeat this process, they're now back in order.
    </details>

- **33**: *Stack with a queue*.
  Implement a stack with a single queue so that each stack operations takes a linear number of queue operations.
  - <details><summary><em>Hint:</em></summary>
    To delete an item, get all of the elements on the queue one at a time, and put them at the end, except for the last one which you should delete and return.
    (Note that this is a very inefficient solution.)
    </details>

**Linked list exercises from Sedgewick & Wayne**

- **1.3.26**:
  Write a method `remove(list, key)` that takes a linked list and a string key as arguments and removes all of the nodes in the list that have the key as its item field.

- **1.3.27**:
  Write a method `max(node)` that takes a reference to the first **Node** in a linked list as argument and returns the value of the maximum key in the list.
  Assume that all keys are positive integers, and return 0 if the list is empty.

- **1.3.30**:
  Write a function that takes the first **Node** in a linked list as argument and (destructively) reverses the list, returning the first **Node** in the result.

**Creative problems from Sedgewick & Wayne**

- **1.3.33**:
  A double-ended queue or *deque* is like a stack or a queue but supports adding and removing items at both ends.
  (See the lecture video "*2D.2 Ordered collections*" for an example API).
  Write a class **LinkedDeque** that uses a doubly-linked list to implement deques.
  Write another class **DynamicArrayDeque** that uses a dynamic array to implement deques.

- **1.3.37**:
  In the [Josephus problem](https://en.wikipedia.org/wiki/Josephus_problem) from antiquity, *N* people are in dire straits and agree to the following strategy to reduce the population.
  They arrange themselves in a circle (at positions numbered from 0 to *N*–1) and proceed around the circle, eliminating every *M*<sup>th</sup> person until only one person is left.
  Legend has it that Josephus figured out where to sit to avoid being eliminated.
  Write a **Queue** client that takes *M* and *N* as input and prints out the order in which people are eliminated (and thus would show Josephus where to sit in the circle).
