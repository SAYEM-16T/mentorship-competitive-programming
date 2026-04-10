# ICT 1101 – Structured Programming Language

## Detailed Answers to the 20 Written Questions

---

## 1) What is an algorithm? Describe the characteristics of a good algorithm with suitable examples.

**Answer:**
An **algorithm** is a finite sequence of clear, logical, and well-defined steps used to solve a problem or perform a task.

In programming, before writing code, we first think about **how the problem will be solved step by step**. That step-by-step plan is called an algorithm.

For example, to find the sum of two numbers:

1. Start
2. Input the first number
3. Input the second number
4. Add the two numbers
5. Display the result
6. Stop

This is an algorithm.

### Characteristics of a good algorithm

**1. Definiteness**
Every step of the algorithm must be clear and unambiguous.
There should be no confusion about what to do.

Example:
“Add the two numbers” is clear.
“Do something with the numbers” is unclear.

**2. Finiteness**
An algorithm must end after a finite number of steps.
It should not continue forever.

Example:
A loop that runs endlessly without a stopping condition is not a proper algorithm.

**3. Input**
A good algorithm may take zero or more inputs.

Example:
To find the average of three numbers, the inputs are the three numbers.

**4. Output**
An algorithm must produce at least one output or result.

Example:
If the task is to find the largest number, the output is that largest value.

**5. Effectiveness**
Each step should be simple, practical, and executable in a reasonable amount of time.

**6. Correctness**
The algorithm must produce the right output for valid input.

**7. Generality**
A good algorithm should solve not just one specific case, but a whole class of similar problems.

Example:
An algorithm to add any two numbers is better than one that adds only 5 and 7.

### Example of an algorithm

**Problem:** Find the larger of two numbers.

**Algorithm:**

1. Start
2. Input A and B
3. If A > B, print A
4. Otherwise, print B
5. Stop

So, an algorithm is the logical foundation of programming.

---

## 2) Explain top-down design and stepwise refinement. How do they help in solving programming problems?

**Answer:**
**Top-down design** is a problem-solving approach in which a large and complex problem is divided into smaller and simpler parts. Instead of solving the entire problem at once, we break it into subproblems.

**Stepwise refinement** is the process of gradually expanding those smaller parts into more detailed steps until they are ready to be coded.

### Top-down design

Suppose we want to build a student result processing program. Instead of writing the full program immediately, we divide the work into parts:

* Take student information
* Take subject marks
* Calculate total and average
* Decide grade
* Display result

This is top-down design.

### Stepwise refinement

Now each part is further broken down.

For example, “Calculate grade” can be refined into:

* If average >= 80, grade = A+
* Else if average >= 70, grade = A
* Else if average >= 60, grade = A-
* Else grade = lower grade

This is stepwise refinement.

### How they help in solving problems

**1. Makes a big problem easier**
A complex problem becomes manageable when divided into smaller pieces.

**2. Improves understanding**
It helps the programmer understand the structure of the solution clearly.

**3. Reduces errors**
Since each part is developed separately, mistakes are easier to find and fix.

**4. Makes coding easier**
Once the logic is refined, writing the actual program becomes straightforward.

**5. Improves readability and maintenance**
A well-designed program is easier to read, test, debug, and modify.

### Example

**Problem:** Find the sum and average of 5 numbers.

**Top-down design:**

* Input 5 numbers
* Calculate sum
* Calculate average
* Display results

**Stepwise refinement:**

* Set sum = 0
* Repeat 5 times:

  * input number
  * add number to sum
* average = sum / 5
* print sum and average

Thus, top-down design and stepwise refinement help us solve programming problems in a structured and organized way.

---

## 3) What is a flowchart? Draw and explain the common flowchart symbols used in program design.

**Answer:**
A **flowchart** is a graphical representation of an algorithm or program logic using standard symbols connected by arrows.

It helps programmers understand the sequence of operations visually before writing code.

### Importance of a flowchart

* Makes logic easy to understand
* Helps in planning the solution
* Reduces mistakes before coding
* Makes debugging easier
* Useful for communication and teaching

### Common flowchart symbols

**1. Terminal / Start-End symbol (Oval)**
Used to indicate the **start** and **end** of a program.

Example:

* Start
* Stop

**2. Process symbol (Rectangle)**
Used for calculations or processing steps.

Example:

* sum = a + b
* i = i + 1

**3. Input/Output symbol (Parallelogram)**
Used for taking input or displaying output.

Example:

* Input A, B
* Print sum

**4. Decision symbol (Diamond)**
Used when a condition is tested and the flow splits into two or more paths.

Example:

* Is A > B?
* Is n even?

**5. Flow line / Arrow**
Used to show the direction of execution.

**6. Connector (Circle)**
Used to connect different parts of a flowchart, especially when the chart is large.

### Example flowchart idea for adding two numbers

Start → Input A, B → Sum = A + B → Print Sum → Stop

So, a flowchart is a visual tool used to represent program logic clearly and systematically.

---

## 4) Write an algorithm and draw a flowchart to find the largest among three numbers.

**Answer:**

### Algorithm

1. Start
2. Input three numbers A, B, and C
3. If A > B and A > C, then Largest = A
4. Else if B > A and B > C, then Largest = B
5. Else Largest = C
6. Print Largest
7. Stop

### Flowchart (text form)

```text
Start
  ↓
Input A, B, C
  ↓
Is A > B and A > C?
  ├── Yes → Largest = A
  │          ↓
  │       Print Largest
  │          ↓
  │         Stop
  │
  └── No → Is B > A and B > C?
             ├── Yes → Largest = B
             │          ↓
             │       Print Largest
             │          ↓
             │         Stop
             │
             └── No → Largest = C
                        ↓
                     Print Largest
                        ↓
                       Stop
```

### Explanation

First we take three inputs. Then we compare them.
If A is greater than both B and C, then A is the largest.
Otherwise, if B is greater than both A and C, then B is the largest.
If neither of those conditions is true, then C must be the largest.

This is a standard decision-making problem in programming.

---

## 5) Discuss the basic structure of a C program. Explain the roles of variables, data types, operators, and expressions.

**Answer:**
A C program is written in a structured way. The basic structure usually includes:

1. Preprocessor directives
2. Main function
3. Variable declarations
4. Statements and expressions
5. Output / return statement

### Basic structure of a C program

```c
#include <stdio.h>

int main() {
    int a, b, sum;
    a = 10;
    b = 20;
    sum = a + b;
    printf("Sum = %d", sum);
    return 0;
}
```

### Explanation of the structure

**1. `#include <stdio.h>`**
This is a header file. It allows us to use functions like `printf()` and `scanf()`.

**2. `int main()`**
This is the main function. Program execution starts from here.

**3. Variable declarations**
Example:

```c
int a, b, sum;
```

These variables store data used in the program.

**4. Statements**
Statements are instructions executed by the computer.

**5. `return 0;`**
Indicates that the program ended successfully.

### Variables

A **variable** is a named memory location used to store data.

Example:

```c
int age;
float salary;
char grade;
```

Variables allow the program to store and manipulate values.

### Data types

A **data type** tells the compiler what kind of value a variable will store.

Common data types in C:

* `int` for integer values
* `float` for decimal values
* `double` for large decimal values
* `char` for a single character

### Operators

**Operators** are symbols used to perform operations.

Examples:

* Arithmetic: `+`, `-`, `*`, `/`, `%`
* Relational: `>`, `<`, `==`, `!=`
* Logical: `&&`, `||`, `!`
* Assignment: `=`

### Expressions

An **expression** is a combination of variables, constants, and operators that gives a value.

Example:

```c
sum = a + b;
```

Here `a + b` is an expression.

So, variables store data, data types define the nature of data, operators perform operations, and expressions combine them to produce results.

---

## 6) What are decision-making statements in C? Explain `if`, `if-else`, and nested `if` with syntax and examples.

**Answer:**
Decision-making statements are used in C to choose different actions depending on whether a condition is true or false.

These statements make a program intelligent because they allow it to respond differently in different situations.

### 1. `if` statement

The `if` statement executes a block only when the condition is true.

**Syntax:**

```c
if (condition) {
    statements;
}
```

**Example:**

```c
#include <stdio.h>
int main() {
    int n = 5;
    if (n > 0) {
        printf("Positive number");
    }
    return 0;
}
```

### 2. `if-else` statement

The `if-else` statement is used when one block should run if the condition is true, and another block should run if it is false.

**Syntax:**

```c
if (condition) {
    statements1;
} else {
    statements2;
}
```

**Example:**

```c
#include <stdio.h>
int main() {
    int n;
    scanf("%d", &n);

    if (n % 2 == 0) {
        printf("Even");
    } else {
        printf("Odd");
    }
    return 0;
}
```

### 3. Nested `if`

A nested `if` means an `if` statement inside another `if` or `else`.

**Example:**

```c
#include <stdio.h>
int main() {
    int a = 10, b = 20, c = 15;

    if (a > b) {
        if (a > c)
            printf("A is largest");
        else
            printf("C is largest");
    } else {
        if (b > c)
            printf("B is largest");
        else
            printf("C is largest");
    }

    return 0;
}
```

### Importance

Decision-making statements are used in many programs such as:

* checking pass or fail
* finding the largest number
* checking positive or negative
* validating input

Thus, decision-making statements help a program take action according to conditions.

---

## 7) Differentiate between `if-else` and `switch` statements. Which one is more suitable in different situations? Explain with examples.

**Answer:**
Both `if-else` and `switch` are used for decision making, but they are suitable in different situations.

### Differences between `if-else` and `switch`

**1. Type of condition**

* `if-else` can handle complex conditions using relational and logical operators.
* `switch` checks only one expression against fixed constant values.

**2. Use of ranges**

* `if-else` can be used for ranges like marks >= 80.
* `switch` cannot directly handle ranges.

**3. Readability**

* For many fixed choices, `switch` is often cleaner and easier to read.
* For complex conditions, `if-else` is better.

**4. Supported values**

* `switch` generally works with integer-type expressions like `int` and `char`.
* `if-else` works with any expression that gives true or false.

### Example of `if-else`

```c
#include <stdio.h>
int main() {
    int marks;
    scanf("%d", &marks);

    if (marks >= 80)
        printf("A+");
    else if (marks >= 70)
        printf("A");
    else if (marks >= 60)
        printf("A-");
    else
        printf("Below A-");

    return 0;
}
```

This is suitable because it uses ranges.

### Example of `switch`

```c
#include <stdio.h>
int main() {
    int day;
    scanf("%d", &day);

    switch(day) {
        case 1: printf("Sunday"); break;
        case 2: printf("Monday"); break;
        case 3: printf("Tuesday"); break;
        default: printf("Invalid");
    }

    return 0;
}
```

This is suitable because the program chooses from fixed values.

### Which one is more suitable?

* Use **`if-else`** for:

  * ranges
  * multiple logical conditions
  * complex comparisons

* Use **`switch`** for:

  * menu-driven programs
  * fixed choices
  * exact constant matching

So, both are important, but the correct choice depends on the problem.

---

## 8) Write a C program to check whether a given year is a leap year or not. Explain the logic of the program.

**Answer:**
A year is a leap year if:

* it is divisible by 400, or
* it is divisible by 4 but not divisible by 100

### Program

```c
#include <stdio.h>

int main() {
    int year;
    scanf("%d", &year);

    if ((year % 400 == 0) || (year % 4 == 0 && year % 100 != 0)) {
        printf("%d is a leap year.\n", year);
    } else {
        printf("%d is not a leap year.\n", year);
    }

    return 0;
}
```

### Logic explanation

We use the remainder operator `%` to check divisibility.

* `year % 400 == 0` means the year is divisible by 400
* `year % 4 == 0` means divisible by 4
* `year % 100 != 0` means not divisible by 100

Examples:

* 2000 is a leap year because it is divisible by 400
* 2024 is a leap year because divisible by 4 and not by 100
* 1900 is not a leap year because although divisible by 100, it is not divisible by 400

This is a common real-life example of decision making in C.

---

## 9) Write a C program to find the largest among three numbers using decision-making statements.

**Answer:**

### Program

```c
#include <stdio.h>

int main() {
    int a, b, c;

    scanf("%d %d %d", &a, &b, &c);

    if (a >= b && a >= c) {
        printf("Largest = %d\n", a);
    } else if (b >= a && b >= c) {
        printf("Largest = %d\n", b);
    } else {
        printf("Largest = %d\n", c);
    }

    return 0;
}
```

### Explanation

The program takes three numbers as input.

Then it compares them:

* If `a` is greater than or equal to both `b` and `c`, then `a` is the largest
* Otherwise, if `b` is greater than or equal to both `a` and `c`, then `b` is the largest
* Otherwise, `c` is the largest

The use of `>=` also handles equal values properly.

This program is an example of multiple-condition decision making using `if-else if-else`.

---

## 10) What is looping in C? Explain the `for`, `while`, and `do-while` loops with syntax and examples.

**Answer:**
Looping in C means repeating a block of code multiple times until a condition becomes false.

Loops are useful when the same task needs to be done again and again, such as printing numbers, summing values, processing arrays, and reading input repeatedly.

### 1. `for` loop

Used when the number of iterations is known in advance.

**Syntax:**

```c
for (initialization; condition; update) {
    statements;
}
```

**Example:**

```c
#include <stdio.h>
int main() {
    int i;
    for (i = 1; i <= 5; i++) {
        printf("%d ", i);
    }
    return 0;
}
```

### 2. `while` loop

Used when the condition is checked before each repetition, and the number of repetitions may not be known beforehand.

**Syntax:**

```c
while (condition) {
    statements;
}
```

**Example:**

```c
#include <stdio.h>
int main() {
    int i = 1;
    while (i <= 5) {
        printf("%d ", i);
        i++;
    }
    return 0;
}
```

### 3. `do-while` loop

In this loop, the body is executed first, and then the condition is checked. So it runs at least once.

**Syntax:**

```c
do {
    statements;
} while (condition);
```

**Example:**

```c
#include <stdio.h>
int main() {
    int i = 1;
    do {
        printf("%d ", i);
        i++;
    } while (i <= 5);
    return 0;
}
```

### Main difference

* `for` → best when count is known
* `while` → best when condition-controlled
* `do-while` → body executes at least once

Loops are essential for efficient programming because they reduce repetition and make programs shorter and smarter.

---

## 11) Differentiate between `for` loop, `while` loop, and `do-while` loop. Mention at least two suitable use cases for each.

**Answer:**

### Difference between `for`, `while`, and `do-while`

**1. `for` loop**

* Initialization, condition, and update are written in one line
* Best when the number of iterations is known

**2. `while` loop**

* Condition is checked before execution
* Best when repetitions depend on a condition and the exact number is unknown

**3. `do-while` loop**

* Condition is checked after execution
* Executes at least once

### Comparison table in idea form

* `for` → entry-controlled, count-based
* `while` → entry-controlled, condition-based
* `do-while` → exit-controlled, minimum one execution

### Suitable use cases

#### `for` loop use cases

1. Printing numbers from 1 to 100
2. Traversing an array with a fixed size

Example:

```c
for (i = 0; i < 10; i++)
```

#### `while` loop use cases

1. Reading data until a sentinel value is entered
2. Repeating until a user gives valid input

Example:

```c
while (n != 0)
```

#### `do-while` loop use cases

1. Menu-driven program that must display the menu at least once
2. Asking for password/input at least one time

Example:

```c
do {
   // menu
} while(choice != 0);
```

### Conclusion

All three loops are useful. The choice depends on the nature of repetition:

* fixed count → `for`
* unknown count but condition-based → `while`
* must run at least once → `do-while`

---

## 12) Write a C program to print the multiplication table of a given number using a loop. Explain how the loop works.

**Answer:**

### Program

```c
#include <stdio.h>

int main() {
    int n, i;
    scanf("%d", &n);

    for (i = 1; i <= 10; i++) {
        printf("%d x %d = %d\n", n, i, n * i);
    }

    return 0;
}
```

### Explanation

The program first takes a number `n` as input.

Then a `for` loop runs from `i = 1` to `i = 10`.

In each iteration:

* the program multiplies `n` by `i`
* then prints the result

For example, if input is `5`, output will be:

* 5 x 1 = 5
* 5 x 2 = 10
* ...
* 5 x 10 = 50

### How the loop works

* **Initialization:** `i = 1`
* **Condition:** `i <= 10`
* **Update:** `i++`

So the loop executes exactly 10 times.

This is a simple example of using loops to generate repeated output.

---

## 13) Write a C program to find the sum of the first `n` natural numbers using a loop. Explain the program step by step.

**Answer:**

### Program

```c
#include <stdio.h>

int main() {
    int n, i, sum = 0;
    scanf("%d", &n);

    for (i = 1; i <= n; i++) {
        sum = sum + i;
    }

    printf("Sum = %d\n", sum);
    return 0;
}
```

### Step-by-step explanation

Suppose the input is `5`.

**Step 1:** Input `n = 5`
**Step 2:** Set `sum = 0`

Now the loop runs:

* `i = 1` → `sum = 0 + 1 = 1`
* `i = 2` → `sum = 1 + 2 = 3`
* `i = 3` → `sum = 3 + 3 = 6`
* `i = 4` → `sum = 6 + 4 = 10`
* `i = 5` → `sum = 10 + 5 = 15`

Then the loop stops and prints `Sum = 15`.

### Purpose

This program demonstrates:

* looping
* accumulation
* variable updating

It is a fundamental programming problem often used to teach repetition and arithmetic logic.

---

## 14) What is an array? Explain one-dimensional arrays in C with declaration, initialization, and example.

**Answer:**
An **array** is a collection of elements of the same data type stored in contiguous memory locations under one variable name.

It is used when we want to store multiple values of the same type without declaring many separate variables.

### One-dimensional array

A **one-dimensional array** stores elements in a single row or list.

### Declaration

Syntax:

```c
data_type array_name[size];
```

Example:

```c
int marks[5];
```

This declares an integer array named `marks` that can store 5 integers.

### Initialization

Arrays can be initialized at the time of declaration.

Example:

```c
int marks[5] = {80, 75, 90, 85, 88};
```

If size is omitted:

```c
int marks[] = {80, 75, 90};
```

### Accessing elements

Array elements are accessed using indexes.

Example:

* `marks[0]` → first element
* `marks[1]` → second element

In C, array indexing starts from `0`.

### Example program

```c
#include <stdio.h>

int main() {
    int a[5] = {10, 20, 30, 40, 50};
    int i;

    for (i = 0; i < 5; i++) {
        printf("%d ", a[i]);
    }

    return 0;
}
```

### Explanation

The array stores 5 values. A loop is used to print each element one by one.

### Advantages of arrays

* store many values under one name
* easier processing using loops
* useful in searching and sorting
* reduces code repetition

Thus, one-dimensional arrays are very important for handling lists of data in C.

---

## 15) Write a C program to input 10 numbers into an array and find the largest and smallest elements.

**Answer:**

### Program

```c
#include <stdio.h>

int main() {
    int a[10], i, largest, smallest;

    for (i = 0; i < 10; i++) {
        scanf("%d", &a[i]);
    }

    largest = a[0];
    smallest = a[0];

    for (i = 1; i < 10; i++) {
        if (a[i] > largest) {
            largest = a[i];
        }
        if (a[i] < smallest) {
            smallest = a[i];
        }
    }

    printf("Largest = %d\n", largest);
    printf("Smallest = %d\n", smallest);

    return 0;
}
```

### Explanation

First, the program takes 10 numbers as input and stores them in an array.

Then:

* `largest` and `smallest` are both initially set to the first element
* the loop checks each remaining element
* if an element is greater than `largest`, it becomes the new largest
* if an element is smaller than `smallest`, it becomes the new smallest

This is a common array-processing problem.

---

## 16) What is the difference between searching and sorting in arrays? Explain linear search and sorting with examples.

**Answer:**
Both searching and sorting are important operations on arrays, but they do different jobs.

### Searching

Searching means finding whether a specific element exists in the array, and if it exists, determining its position.

Example:
Find whether `25` exists in the array.

### Sorting

Sorting means arranging elements in a specific order, usually ascending or descending.

Example:
Arrange `40, 10, 30, 20` as `10, 20, 30, 40`.

### Difference

* Searching finds an item
* Sorting arranges items

### Linear search

Linear search checks each element one by one from the beginning until the target is found or the array ends.

**Example program:**

```c
#include <stdio.h>

int main() {
    int a[5] = {10, 20, 30, 40, 50};
    int key = 30, i, found = 0;

    for (i = 0; i < 5; i++) {
        if (a[i] == key) {
            found = 1;
            printf("Found at index %d\n", i);
            break;
        }
    }

    if (!found) {
        printf("Not found\n");
    }

    return 0;
}
```

### Simple sorting example

A common sorting technique is **bubble sort**.

```c
#include <stdio.h>

int main() {
    int a[5] = {40, 10, 30, 20, 50};
    int i, j, temp;

    for (i = 0; i < 4; i++) {
        for (j = 0; j < 4 - i; j++) {
            if (a[j] > a[j + 1]) {
                temp = a[j];
                a[j] = a[j + 1];
                a[j + 1] = temp;
            }
        }
    }

    for (i = 0; i < 5; i++) {
        printf("%d ", a[i]);
    }

    return 0;
}
```

### Explanation

* Linear search checks one by one
* Sorting rearranges the full array
* Searching helps find data
* Sorting helps organize data for easier use

---

## 17) Explain two-dimensional arrays in C. Write a program to input and display a 3×3 matrix.

**Answer:**
A **two-dimensional array** is an array that stores data in rows and columns. It is often used to represent a matrix or table.

### Declaration

Syntax:

```c
data_type array_name[row][column];
```

Example:

```c
int a[3][3];
```

This creates a matrix with 3 rows and 3 columns.

### Accessing elements

Elements are accessed using two indexes:

```c
a[i][j]
```

where `i` is the row index and `j` is the column index.

### Program to input and display a 3×3 matrix

```c
#include <stdio.h>

int main() {
    int a[3][3], i, j;

    for (i = 0; i < 3; i++) {
        for (j = 0; j < 3; j++) {
            scanf("%d", &a[i][j]);
        }
    }

    printf("Matrix:\n");
    for (i = 0; i < 3; i++) {
        for (j = 0; j < 3; j++) {
            printf("%d ", a[i][j]);
        }
        printf("\n");
    }

    return 0;
}
```

### Explanation

The first nested loop takes input row by row.
The second nested loop prints the matrix row by row.

### Uses of 2D arrays

* matrices
* tables
* game boards
* grid-based data

Thus, two-dimensional arrays are very useful when data naturally fits into rows and columns.

---

## 18) What is a character? What is a string in C? Explain how strings are stored in memory.

**Answer:**
A **character** in C is a single symbol stored using the `char` data type.

Example:

```c
char ch = 'A';
```

A **string** is a sequence of characters terminated by the null character `'\0'`.

Example:

```c
char name[] = "Hello";
```

### Difference between character and string

* Character → one symbol, enclosed in single quotes
* String → multiple characters, enclosed in double quotes

Examples:

```c
char ch = 'A';
char str[] = "A";
```

### How strings are stored in memory

Strings are stored as **character arrays**.

For example:

```c
char str[] = "Hello";
```

In memory, it is stored as:

* `H`
* `e`
* `l`
* `l`
* `o`
* `\0`

The null character `\0` marks the end of the string.

### Why `\0` is important

Functions like `printf("%s", str)` continue reading characters until they find `\0`. Without it, the string would not be recognized properly.

### Example

```c
#include <stdio.h>

int main() {
    char name[] = "C Program";
    printf("%s\n", name);
    return 0;
}
```

### Conclusion

A character is a single unit of text, while a string is a collection of characters stored in a character array and terminated by `'\0'`.

---

## 19) Discuss common string handling functions in C such as `strlen()`, `strcpy()`, `strcat()`, and `strcmp()` with examples.

**Answer:**
In C, many useful string functions are available in the header file `string.h`.

So, to use them, we write:

```c
#include <string.h>
```

### 1. `strlen()`

This function returns the length of a string, excluding the null character.

**Example:**

```c
#include <stdio.h>
#include <string.h>

int main() {
    char str[] = "Hello";
    printf("%lu\n", strlen(str));
    return 0;
}
```

**Output:**
`5`

### 2. `strcpy()`

This function copies one string into another.

**Example:**

```c
#include <stdio.h>
#include <string.h>

int main() {
    char source[] = "Programming";
    char destination[20];

    strcpy(destination, source);

    printf("%s\n", destination);
    return 0;
}
```

### 3. `strcat()`

This function appends one string to the end of another.

**Example:**

```c
#include <stdio.h>
#include <string.h>

int main() {
    char a[20] = "Hello ";
    char b[] = "World";

    strcat(a, b);

    printf("%s\n", a);
    return 0;
}
```

**Output:**
`Hello World`

### 4. `strcmp()`

This function compares two strings.

**Example:**

```c
#include <stdio.h>
#include <string.h>

int main() {
    char a[] = "apple";
    char b[] = "apple";

    if (strcmp(a, b) == 0)
        printf("Equal\n");
    else
        printf("Not equal\n");

    return 0;
}
```

### Return values of `strcmp()`

* `0` → strings are equal
* negative → first string is smaller
* positive → first string is greater

### Importance of string functions

These functions make string handling easier in C:

* measuring length
* copying strings
* joining strings
* comparing strings

Since strings are character arrays in C, these functions are extremely useful in text processing.

---

## 20) Write a C program to input a string and count the number of vowels, consonants, digits, and spaces in it.

**Answer:**

### Program

```c
#include <stdio.h>

int main() {
    char str[200];
    int i = 0, vowels = 0, consonants = 0, digits = 0, spaces = 0;

    fgets(str, sizeof(str), stdin);

    while (str[i] != '\0') {
        char ch = str[i];

        if (ch >= 'A' && ch <= 'Z') {
            ch = ch + 32;   // convert to lowercase
        }

        if (ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u') {
            vowels++;
        } else if (ch >= 'a' && ch <= 'z') {
            consonants++;
        } else if (ch >= '0' && ch <= '9') {
            digits++;
        } else if (ch == ' ') {
            spaces++;
        }

        i++;
    }

    printf("Vowels = %d\n", vowels);
    printf("Consonants = %d\n", consonants);
    printf("Digits = %d\n", digits);
    printf("Spaces = %d\n", spaces);

    return 0;
}
```

### Explanation

The program takes a full line of text using `fgets()`.

Then it checks each character one by one:

* if it is `a, e, i, o, u` → vowel count increases
* if it is another alphabet letter → consonant count increases
* if it is a digit → digit count increases
* if it is a blank space → space count increases

### Example

If input is:

```text
Hello 123 World
```

Then:

* vowels = 3 (`e`, `o`, `o`)
* consonants = 7
* digits = 3
* spaces = 2

This program demonstrates string traversal and character classification.
