# Day 01 — Introduction to Data Structures

## Course Context
- **Course Code:** ICT 2101
- **Course Title:** Data Structures
<!-- - **Semester:** 2nd Year, 1st Semester -->
- **Language Plan:** Python for main explanation, C++ only for comparison when needed

## Day 01 Topics
- Types of Data Structure
- Basic Concepts of Algorithm
- Programming Principle
- ADT
- Class

## Learning Objectives
By the end of this class, students should be able to:
- define data and data structure
- explain why data structures are needed
- distinguish between data structures and algorithms
- identify major types of data structures
- understand the idea of ADT
- understand the difference between logical design and implementation
- connect class-based modeling with ADT

## Prerequisite Reminder
Students are expected to already know:
- variables
- arrays
- functions
- basic searching and sorting ideas
- basic memory idea from previous programming courses

## 1. What is Data?
Data is a collection of raw values or facts.

Examples:
- roll number
- marks
- names
- temperature readings
- product prices

By itself, data may not be very useful unless it is organized properly.

## 2. What is a Data Structure?
A data structure is a way of organizing, storing, and managing data so that it can be used efficiently.

### Simple idea
If data is the "things",
then data structure is the "way we arrange those things".

### Example
If we store student names:
- in a simple list
- in a tree
- in a hash table

the data is the same, but access pattern and efficiency change.

## 3. Why Do We Need Data Structures?
We need data structures because:
- data size becomes large
- searching can become slow
- insertion and deletion may become difficult
- different problems need different organization methods
- efficient programs depend on proper data organization

## 4. Data Structure vs Algorithm
### Data Structure
A way to organize data.

### Algorithm
A step-by-step procedure to solve a problem.

### Relationship
A program solves a problem using:
- data structure for storing data
- algorithm for processing data

## 5. Types of Data Structure

### 5.1 Linear Data Structure
In linear data structures, elements are arranged sequentially.

Examples:
- array
- linked list
- stack
- queue

#### Characteristics
- one element is followed by another
- traversal is straightforward
- easy to visualize in a line

### 5.2 Non-linear Data Structure
In non-linear data structures, elements are not arranged in one straight sequence.

Examples:
- tree
- graph
- heap
- hash table

#### Characteristics
- hierarchical or network-like relation
- more flexible structure
- useful for complex relationships

### 5.3 Static vs Dynamic Data Structure

#### Static
Size is fixed in advance.

Example:
- array with fixed size

#### Dynamic
Size can grow or shrink during runtime.

Example:
- linked list

### 5.4 Homogeneous vs Non-homogeneous

#### Homogeneous
All elements are of the same type.

Example:
- list of integers

#### Non-homogeneous
Different types of data can be grouped together.

Example:
- student record with name, id, cgpa

## 6. Basic Concepts of Algorithm

### 6.1 Definition
An algorithm is a finite sequence of well-defined steps used to solve a problem.

### 6.2 Properties of a Good Algorithm
A good algorithm should have:
- input
- output
- finiteness
- definiteness
- effectiveness

### 6.3 Simple Example
Problem: Find the maximum of three numbers.

Steps:
1. Take three numbers
2. Compare first two
3. Compare the larger one with the third
4. Print the largest

## 7. Programming Principle
In data structures, programming principle means writing code that is:
- clear
- modular
- reusable
- correct
- efficient

### Important ideas
- break a big problem into smaller parts
- use functions or methods
- choose meaningful names
- separate logic from implementation details
- test with different inputs

## 8. What is ADT?
ADT means **Abstract Data Type**.

An ADT defines:
- what data is stored
- what operations are allowed

But it does **not** define:
- how those operations are internally implemented

### Example: Stack ADT
Operations:
- push
- pop
- top
- is_empty

But ADT does not say whether stack is implemented using:
- array
- linked list

## 9. ADT vs Data Structure
### ADT
Logical view

### Data Structure
Physical / implementation view

### Example
Stack is an ADT  
Array-based stack is a data structure implementation  
Linked-list-based stack is another implementation

## 10. Class and ADT
A class can be used to implement an ADT.

### Why class is useful
- combines data and methods
- supports encapsulation
- makes code reusable
- keeps implementation organized

### Example idea
A `Stack` class may contain:
- internal storage
- `push()`
- `pop()`
- `peek()`

## 11. Real-life Examples
- Browser back button → stack
- Print queue → queue
- Folder system → tree
- Social network connection → graph
- Phone contacts lookup → hashing

## 12. In-class Discussion Questions
1. কেন array সব problem-এর জন্য best না?
2. Stack আর queue-এর difference কী?
3. ADT আর actual implementation-এর difference কী?
4. একই problem-এর জন্য different data structure কেন লাগতে পারে?

## 13. Board Work / Whiteboard Plan
- Data vs Data Structure
- Data Structure vs Algorithm
- Linear vs Non-linear
- Static vs Dynamic
- ADT idea
- Class as implementation tool

## 14. Suggested Classroom Flow
- 10 min: course intro
- 15 min: data structure basics
- 15 min: algorithm basics
- 15 min: types of data structure
- 15 min: ADT and class
- 10 min: real-life examples and Q/A

## 15. Quick Recap
- Data structure organizes data
- Algorithm processes data
- Different problems need different structures
- ADT gives logical design
- Class helps implementation

## Homework
1. Write definitions of:
   - data
   - data structure
   - algorithm
   - ADT
2. Give 2 examples of linear and 2 examples of non-linear data structures
3. Explain the difference between ADT and data structure with one example
4. Write 5 real-life examples where a data structure is needed