
## 1. What is Backtracking?

**Backtracking** is a recursive algorithmic technique for solving problems incrementally by building partial solutions, exploring possible choices, and discarding a solution as soon as it cannot lead to a valid answer.

### 🧠 Example — Finding All Pairs

Suppose we have:

    [2, 3]

We want to explore all possible choices and find the pair:

    [2, 3]

whose sum is:

    2 + 3 = 5

At every element, we have two choices:

    Take the element
          OR
    Skip the element

This creates a **decision tree**:

                         []
                       /    \
                   Take 2   Skip 2
                     [2]       []
                    /   \
              Take 3   Skip 3
               [2,3]     [2]
                 ↓         ↓
               2 + 3       —
                 ↓
                  5

The path:

    [] → [2] → [2,3]

produces the pair:

    [2,3]

and therefore:

    2 + 3 = 5

### 🔄 What is Backtracking Here?

After exploring:

    [2,3]

we **go back** and remove `3`:

    [2,3]
       ↓
    remove 3
       ↓
      [2]

Then we can explore the next choice.

Similarly, after finishing all choices involving `2`, we go back and remove `2`:

    [2]
     ↓
    remove 2
     ↓
     []

Now we can explore choices starting without `2`.

### 🔑 Core Pattern

    Choose
      ↓
    Explore recursively
      ↓
    Undo the choice
      ↓
    Explore another choice

### ⭐ Golden Rule

> **Backtracking explores a decision tree by making choices step-by-step, and whenever a branch is finished or cannot lead to a valid solution, it goes back to the previous state and tries another choice.**

---

## 2. Use Cases of Backtracking

Backtracking is useful when a problem requires us to **explore multiple possible choices** and find one or more valid solutions.

The most common use cases are:

### 1. 🔢 Subsets

Generate all possible subsets of an array.

Example:

    [1, 2]

Possible subsets:

    []
    [1]
    [2]
    [1,2]

At each element:

    Take it
       OR
    Skip it

---

### 2. 🔄 Permutations

Generate all possible arrangements of elements.

Example:

    [1, 2, 3]

Possible permutations include:

    [1,2,3]
    [1,3,2]
    [2,1,3]
    [2,3,1]
    [3,1,2]
    [3,2,1]

At each step:

    Choose one unused element
          ↓
    Recursively choose the next element

---

### 3. 🧩 Combinations

Generate all possible groups of a specific size.

Example:

    [1,2,3]
    Choose 2

Possible combinations:

    [1,2]
    [1,3]
    [2,3]

Order does not matter:

    [1,2] = [2,1]

---

### 4. ➕ Combination Sum

Find combinations of numbers that satisfy a target.

Example:

    [2,3,6,7]
    target = 7

Possible answer:

    [2,2,3]
    [7]

We keep making choices while tracking the remaining target.

---

### 5. ♟️ N-Queens

Place `N` queens on an `N × N` chessboard such that no two queens attack each other.

At each row:

    Try placing a queen
          ↓
    Check if position is valid
          ↓
    Continue recursively
          ↓
    If invalid → remove queen
          ↓
    Try another position

---

### 6. 🧩 Sudoku

Fill an incomplete Sudoku board.

At each empty cell:

    Try 1
    Try 2
    Try 3
     ...
    Try 9

If a number violates the Sudoku rules:

    Undo
    ↓
    Try another number

---

### 7. 🗺️ Path Finding / Maze

Find possible paths through a maze.

At every position:

    Move Up
    Move Down
    Move Left
    Move Right

If a path reaches a dead end:

    Go back
       ↓
    Try another direction

---

### 8. 🔤 Word Search

Find whether a word can be formed by connecting adjacent cells.

At every cell:

    Choose the cell
       ↓
    Mark it as visited
       ↓
    Explore neighbors
       ↓
    Unmark it
       ↓
    Try another path

---

### 9. 🧱 Generate Valid Parentheses

Generate all valid combinations of parentheses.

For example:

    n = 2

Output:

    (())
    ()()

At every step we can potentially choose:

    Add "("
       OR
    Add ")"

But invalid choices are **pruned**.

---

### 🔑 General Pattern

Backtracking is a good candidate when the problem has:

    Multiple choices
          ↓
    Build a partial solution
          ↓
    Explore recursively
          ↓
    Check validity
          ↓
    Undo
          ↓
    Try another choice

### ⭐ Golden Rule

> **Think Backtracking whenever you need to explore many possible combinations, arrangements, paths, or configurations and can build the solution one choice at a time.**

---

