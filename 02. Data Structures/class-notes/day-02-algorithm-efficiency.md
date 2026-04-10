# Day 02 — Algorithm Efficiency

## Course Context
- **Course Code:** ICT 2101
- **Course Title:** Data Structures
<!-- - **Semester:** 2nd Year, 1st Semester -->
- **Language Plan:** Python for main explanation

## Day 02 Topics
- Order of Magnitude
- Asymptotic Notations

## Learning Objectives
By the end of this class, students should be able to:
- explain why algorithm efficiency matters
- understand time complexity and space complexity
- compare two algorithms using growth rate
- understand order of magnitude
- understand asymptotic notation
- read simple code and estimate running time

## 1. Why Study Algorithm Efficiency?
Two programs may solve the same problem, but one may:
- take less time
- use less memory
- scale better for large input

Data structures become meaningful only when we can compare performance.

## 2. What is Efficiency?
Efficiency mainly means:
- **time efficiency** → how long the algorithm takes
- **space efficiency** → how much memory it uses

In this class, our main focus is time complexity.

## 3. Input Size
We usually express performance in terms of input size `n`.

Examples:
- number of elements in an array
- number of nodes in a tree
- number of vertices in a graph

## 4. Order of Magnitude
Order of magnitude means the general growth behavior of an algorithm.

We do not focus on:
- small constants
- exact machine time
- programming language overhead

We focus on:
- how running time grows as input size grows

## 5. Example of Growth
Suppose there are three algorithms:
- Algorithm A → `5n`
- Algorithm B → `n^2`
- Algorithm C → `log n`

For small input, the difference may seem small.  
For large input, the difference becomes huge.

## 6. Common Growth Rates
From better to worse, usually:
- `O(1)`
- `O(log n)`
- `O(n)`
- `O(n log n)`
- `O(n^2)`
- `O(n^3)`
- `O(2^n)`
- `O(n!)`

## 7. What is Asymptotic Analysis?
Asymptotic analysis studies algorithm behavior when input size becomes very large.

It helps us compare algorithms in a machine-independent way.

## 8. Big-O Notation
Big-O gives an upper bound on growth.

### Meaning
If an algorithm is `O(n)`, it grows at most linearly for large input.

### Examples
- `3n + 2` → `O(n)`
- `2n^2 + 5n + 7` → `O(n^2)`
- `10 log n + 4` → `O(log n)`

## 9. Ignoring Constants and Lower-order Terms
In asymptotic notation:
- constants are ignored
- lower-order terms are ignored

Examples:
- `100n + 20` → `O(n)`
- `n^2 + 50n + 1` → `O(n^2)`

## 10. Best, Average, and Worst Case
### Best case
The minimum time needed.

### Average case
Expected or typical running time.

### Worst case
The maximum time needed.

In most introductory analysis, we mainly discuss worst-case complexity.

## 11. Time Complexity of Basic Statements

### 11.1 Constant Statement
```python
x = x + 1
```

Time complexity: `O(1)`

### 11.2 Simple Loop

```python
for i in range(n):
    print(i)
```

Time complexity: `O(n)`

### 11.3 Nested Loop

```python
for i in range(n):
    for j in range(n):
        print(i, j)
```

Time complexity: `O(n^2)`

### 11.4 Consecutive Loops

```python
for i in range(n):
    print(i)

for j in range(n):
    print(j)
```

Time complexity: `O(n)`

## 12. Rule of Thumb for Analysis

* one simple operation → `O(1)`
* one loop over `n` elements → `O(n)`
* two nested loops over `n` → `O(n^2)`
* divide by 2 repeatedly → `O(log n)`
* merge-style splitting + processing → `O(n log n)`

## 13. Small Example: Linear Search

If we search for an item in an unsorted list:

* best case → `O(1)`
* worst case → `O(n)`

## 14. Small Example: Binary Search

If we search in a sorted list:

* repeatedly divide search space by 2
* complexity → `O(log n)`

## 15. Why This Matters in Data Structures

Later in this course we will compare:

* array vs linked list
* stack vs queue operations
* BST vs linear search
* hashing vs sequential search

Efficiency gives us the reason to choose one structure over another.

## 16. Mistakes Students Commonly Make

* counting exact seconds instead of growth
* keeping constants in final asymptotic answer
* confusing `O(n)` with `O(n^2)`
* forgetting that nested loops multiply
* forgetting that input must be large for asymptotic meaning

## 17. In-class Exercises

1. Find the complexity:

   * `5n + 3`
   * `n^2 + 2n + 1`
   * `7`
   * `log n + n`
2. Analyze:

   * single loop
   * double loop
   * halving loop
3. Compare which is better for large input:

   * `O(n)` vs `O(n log n)`
   * `O(log n)` vs `O(n)`

## 18. Board Work / Whiteboard Plan

* Order of magnitude
* Growth rate table
* O-notation examples
* loop analysis
* linear search vs binary search

<!-- ## 19. Suggested Classroom Flow

* 10 min: recap of day 1
* 15 min: why efficiency matters
* 15 min: order of magnitude
* 20 min: asymptotic notation
* 15 min: loop-based examples
* 10 min: search comparison
* 5 min: recap -->

## 20. Quick Recap

* Efficiency matters for large input
* Order of magnitude means growth trend
* Big-O ignores constants and smaller terms
* `O(1)`, `O(log n)`, `O(n)`, `O(n log n)`, `O(n^2)` are common
* Complexity helps choose data structures

## Homework

1. Define:

   * time complexity
   * space complexity
   * order of magnitude
   * asymptotic analysis
2. Write Big-O of:

   * `4n + 9`
   * `n^2 + 10n + 5`
   * `6`
   * `3log n + n`
3. Analyze the complexity of:

   * one loop
   * two nested loops
   * loop with `i = i * 2`
4. Explain why binary search is faster than linear search for large sorted input
