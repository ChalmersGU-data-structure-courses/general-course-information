# Exercise solutions: Sequences

Here are suggested solutions to some of the exercises about stacks, queues and lists.

## Core exercises

### A1 + A2. What is the result of running the stack/queue program on the following input: `it was - the best - of times - - - it was - the - -`?

See the solution to question **B1** below and then run it for yourself:)

### A3. Give an algorithm that removes all comments from a program.

The idea is to go through the program and use a counter to track how deeply nested the current position is. This counter behaves like a stack where we don't care about the elements, only the size (instead of push/pop, we increment/decrement).

- <details><summary><em>Try to implement it first, and then you can click here to reveal a solution in pseudocode.</em></summary>

    ```python
    comments = 0
    for each character in program:
        if character == "{":
            comments += 1
        else if character == "}":
            if comments == 0:
                throw error "comment end without start"
            comments -= 1
        else:
            if comments == 0:
                add character to new program
    if comments > 0:
        throw error "comment start without end"
    ```
    </details>

Assuming we use a dynamic array to store the new program, the time complexity of this algorithm is linear in the length of the original program (i.e., O(n)).

For the hard part, we really have to use a stack. There are different kinds of nested comments, `{ ... }` (type A) and `[ ... ]` (type B). When we encounter `{`, we push "A" onto the stack. Similarly, when we encounter `[`, we push "B". When we encounter `}`, we pop from the stack and check that we get "A". Similarly, when we encounter `]`, we pop from the stack and check that we get "B". After going over the whole program, we check that the stack is empty (otherwise we have an unclosed comment).


### A4. Write a program that reads a postfix expression and evaluates it.

[Here's an explanation](http://mathcenter.oxford.emory.edu/site/cs171/postfixExpressions/) of postfix expressions together with a high-level description of the algorithm. The main idea can be summarised as follows:

- Use a stack of numbers
- Read one term at the time:
    - if the term is a number, push it onto the stack
    - if the term is an operator, pop the two topmost numbers, apply the operator to them, and push the result back onto the stack

Solution:

- <details><summary><em>Try to implement it first, and then you can click here to reveal a solution in pseudocode.</em></summary>

  ```python
  stack = new Stack()
  for each token in the input stream:
      if token == ".":
          print stack.pop()
      else if token == "+":
          stack.push(stack.pop() + stack.pop())
      else if token == "+":
          stack.push(stack.pop() + stack.pop())
      else if token == "-":
          stack.push(stack.pop() + stack.pop())
      else if token == "*":
          stack.push(stack.pop() + stack.pop())
      else:
          stack.push(token parsed as an integer)
  ```
  </details>


### A5. Sequence of queue operations

Regardless of the order in which you give the enqueue/dequeue operations, the result will always be the same: the elements are returned in the same order as they were enqueued.

So if you enqueue the numbers 0 to 9, then the only sequence that can occur is 0, 1, …, 9.


### A6. An array of unlimited size

This is a variant of a dynamic array.

- <details><summary><em>Try to implement it first, and then you can click here to reveal a suggestion in pseudocode.</em></summary>

    ```python
    class UnlimitedSizeArray:
        array = new Array of size 1

        get(index):
            return array[index]

        # Here is one way to implement `set`.
        set(index, value):
            # Repeatedly double the array until it's big enough
            while index >= array.size():
                resize(array.size()*2)
            array[index] = value

        # Here is another way. Both ways work!
        set(index, value):
            # If the array is too small, increase its size.
            # But, to avoid having to copy the array too often,
            # at least double the size of the array.
            if index >= array.size():
                resize(max(array.size()*2, index+1))
            array[index] = value

        # A private method to resize the array.
        resize(newSize):
            oldArray = array
            array = new Array of size newSize
            for i in 0 ... array.size()-1:
                array[i] = oldArray[i]
    ```
    </details>

## Bonus exercises

### B1. Implement the programs in A1 and A2.

- <details><summary><em>Try to implement it first, and then you can click here to reveal a suggestion in pseudocode.</em></summary>

    ```python
    stack = new Stack()
    for every word in the input stream:
        if word == "-":
            print(stack.pop())
        else:
            stack.push(word)
    print(stack.size(), "elements left on stack")
    ```
    </details>

### B2. Sequence of stack operations

This is much trickier than **A5**!

Suppose the sequence looks like this: **[…, *a*, …, *b*, …, *c*, …]**, where there might or might not be numbers between ***a***, ***b*** and ***c***. Now, if ***a > b***, ***a > c*** and ***b < c***, then the sequence is impossible!

Informal proof: When ***a*** is popped, we know that both ***b*** and ***c*** must be on the stack (because they are pushed in numerical order). But ***b*** was pushed earlier than ***c*** (because ***b < c***), and therefore ***b*** cannot be popped before ***c*** is popped.

### B3. Exercises from Sedgewick & Wayne

**Heading "Exercises" on the book website**: <https://algs4.cs.princeton.edu/13stacks/>

- **4 + 6**: See the book website

**Heading "Web Exercises" on the book website**: <https://algs4.cs.princeton.edu/13stacks/>

- **31**: See the book website
- **33**: (Left as exercise)

**Linked list exercises from the book**

- **1.3.26**: The important thing to note is that we need to remember the previous list node, because to delete a node we have to redirect the previous node. We also have to give some extra thought to the first list element.

    - <details><summary><em>Click here to show some pseudocode.</em></summary>

        ```python
        previous = null
        current = list.first
        while current is not null:
            if current.item is not equal to key:
                previous = current
            else if previous is null:
                list.first = current.next   # we remove the first element in the list
            else:
                previous.next = current.next   # we remove an inner element
            current = current.next
        ```
        </details>

- **1.3.27**: Loop through the list, keeping the current maximum in a variable.

    - <details><summary><em>Click here to show some pseudocode.</em></summary>

        ```python
        max = 0
        current : Node = list.first
        while current is not null:
            if current.item > max:
                max = current.item
            current = current.next
        ```
        </details>

- **1.3.30**: (See the exercise in Sedgewick & Wayne for two possible solutions)

**Creative problems from the book**

- **1.3.33**: (Left as an exercise)
- **1.3.37**: See the book website: <https://algs4.cs.princeton.edu/13stacks/>
