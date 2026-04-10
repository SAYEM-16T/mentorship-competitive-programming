# Question Bank with Answers

## ICT 1101 – Structured Programming Language

---

# 1. Program Design Fundamentals

## 1. What is programming?

**Answer:**
Programming is the process of writing instructions that tell a computer how to perform a task.

---

## 2. What is a program?

**Answer:**
A program is a set of ordered instructions written in a programming language to solve a specific problem.

---

## 3. What is problem analysis in programming?

**Answer:**
Problem analysis means understanding the problem clearly, identifying the input, process, and output before writing the program.

---

## 4. What is top-down design?

**Answer:**
Top-down design is a problem-solving approach in which a large problem is divided into smaller and simpler subproblems.

---

## 5. What is stepwise refinement?

**Answer:**
Stepwise refinement is the process of gradually breaking a problem into smaller detailed steps until it becomes easy to code.

---

## 6. What is an algorithm?

**Answer:**
An algorithm is a finite sequence of clear and logical steps used to solve a problem.

---

## 7. What are the characteristics of a good algorithm?

**Answer:**
A good algorithm should be:

* clear
* finite
* correct
* efficient
* easy to understand

---

## 8. What is a flowchart?

**Answer:**
A flowchart is a graphical representation of an algorithm using standard symbols.

---

## 9. Why is a flowchart important?

**Answer:**
A flowchart helps us understand program logic visually before coding. It makes problem solving easier and reduces mistakes.

---

## 10. Name some common flowchart symbols.

**Answer:**
Common flowchart symbols are:

* Oval → Start/End
* Rectangle → Process
* Parallelogram → Input/Output
* Diamond → Decision
* Arrow → Flow line

---

## 11. What is meant by input, process, and output?

**Answer:**

* **Input**: data given to the program
* **Process**: operations performed on the data
* **Output**: final result produced by the program

---

## 12. What is a variable?

**Answer:**
A variable is a named memory location used to store data that may change during program execution.

---

## 13. What is a data type?

**Answer:**
A data type specifies the type of data a variable can store, such as integer, float, or character.

---

## 14. Name some basic data types in C.

**Answer:**
Basic data types in C are:

* `int`
* `float`
* `double`
* `char`

---

## 15. What is an operator?

**Answer:**
An operator is a symbol that performs an operation on one or more operands.

---

## 16. What is an expression?

**Answer:**
An expression is a combination of variables, constants, and operators that produces a value.

Example:

```c
a + b * 2
```

---

## 17. What is the difference between an algorithm and a flowchart?

**Answer:**
An algorithm is written in step form using words, while a flowchart shows the same logic using graphical symbols.

---

## 18. Write an algorithm to add two numbers.

**Answer:**

1. Start
2. Input first number
3. Input second number
4. Add the two numbers
5. Display the sum
6. Stop

---

## 19. Write a simple C program to input two numbers and print their sum.

**Answer:**

```c
#include <stdio.h>

int main() {
    int a, b, sum;
    scanf("%d %d", &a, &b);
    sum = a + b;
    printf("Sum = %d", sum);
    return 0;
}
```

---

## 20. Why is program design necessary before coding?

**Answer:**
Program design is necessary because it helps organize the logic, reduce errors, improve readability, and make coding easier.

---

# 2. Control Structures (Decision Making)

## 1. What is a control structure?

**Answer:**
A control structure determines the order in which statements are executed in a program.

---

## 2. What is decision making in programming?

**Answer:**
Decision making means choosing different actions based on whether a condition is true or false.

---

## 3. What is the `if` statement?

**Answer:**
The `if` statement is used to execute a block of code only when a condition is true.

---

## 4. Write the syntax of an `if` statement.

**Answer:**

```c
if (condition) {
    statements;
}
```

---

## 5. What is an `if-else` statement?

**Answer:**
An `if-else` statement is used when one block is executed if the condition is true, and another block is executed if the condition is false.

---

## 6. Write the syntax of `if-else`.

**Answer:**

```c
if (condition) {
    statements1;
} else {
    statements2;
}
```

---

## 7. What is a nested `if` statement?

**Answer:**
A nested `if` statement means using an `if` statement inside another `if` or `else` block.

---

## 8. What is the purpose of the `else if` ladder?

**Answer:**
The `else if` ladder is used to test multiple conditions one after another.

---

## 9. What is the `switch` statement?

**Answer:**
The `switch` statement is used to select one block of code from many alternatives based on the value of an expression.

---

## 10. Write the syntax of a `switch` statement.

**Answer:**

```c
switch (expression) {
    case value1:
        statements;
        break;
    case value2:
        statements;
        break;
    default:
        statements;
}
```

---

## 11. What is the role of `break` in a `switch` statement?

**Answer:**
`break` is used to terminate the current case and exit the switch block.

---

## 12. What happens if `break` is omitted in `switch`?

**Answer:**
If `break` is omitted, execution continues into the next case. This is called fall-through.

---

## 13. What is the `default` case in `switch`?

**Answer:**
The `default` case is executed when none of the case values match the expression.

---

## 14. What is the difference between `if-else` and `switch`?

**Answer:**
`if-else` is used for complex conditions involving ranges and logical operators, while `switch` is mainly used for checking one variable against fixed constant values.

---

## 15. Write a program to check whether a number is positive or negative.

**Answer:**

```c
#include <stdio.h>

int main() {
    int n;
    scanf("%d", &n);

    if (n >= 0)
        printf("Positive");
    else
        printf("Negative");

    return 0;
}
```

---

## 16. Write a program to find the larger of two numbers using `if-else`.

**Answer:**

```c
#include <stdio.h>

int main() {
    int a, b;
    scanf("%d %d", &a, &b);

    if (a > b)
        printf("%d is larger", a);
    else
        printf("%d is larger", b);

    return 0;
}
```

---

## 17. Write a program to check whether a number is even or odd.

**Answer:**

```c
#include <stdio.h>

int main() {
    int n;
    scanf("%d", &n);

    if (n % 2 == 0)
        printf("Even");
    else
        printf("Odd");

    return 0;
}
```

---

## 18. Write a program using `switch` to display the day name for a number from 1 to 3.

**Answer:**

```c
#include <stdio.h>

int main() {
    int day;
    scanf("%d", &day);

    switch (day) {
        case 1:
            printf("Sunday");
            break;
        case 2:
            printf("Monday");
            break;
        case 3:
            printf("Tuesday");
            break;
        default:
            printf("Invalid");
    }

    return 0;
}
```

---

## 19. Can `switch` be used with float values in C?

**Answer:**
No. In C, `switch` does not work with float values. It works with integer-type expressions such as `int` and `char`.

---

## 20. Why are decision-making statements important?

**Answer:**
They make the program intelligent by allowing it to choose actions based on different situations.

---

# 3. Looping / Iteration

## 1. What is a loop?

**Answer:**
A loop is a control structure that repeats a block of code multiple times.

---

## 2. Why are loops used in programming?

**Answer:**
Loops are used to perform repetitive tasks efficiently without writing the same code again and again.

---

## 3. What are the main types of loops in C?

**Answer:**
The main types of loops in C are:

* `for`
* `while`
* `do-while`

---

## 4. What is a `for` loop?

**Answer:**
A `for` loop is used when the number of iterations is known beforehand.

---

## 5. Write the syntax of a `for` loop.

**Answer:**

```c
for (initialization; condition; update) {
    statements;
}
```

---

## 6. What is a `while` loop?

**Answer:**
A `while` loop repeats a block of code as long as the condition remains true.

---

## 7. Write the syntax of a `while` loop.

**Answer:**

```c
while (condition) {
    statements;
}
```

---

## 8. What is a `do-while` loop?

**Answer:**
A `do-while` loop executes the loop body first and checks the condition afterward. So it runs at least once.

---

## 9. Write the syntax of a `do-while` loop.

**Answer:**

```c
do {
    statements;
} while (condition);
```

---

## 10. What is the main difference between `while` and `do-while`?

**Answer:**
In `while`, the condition is checked before execution. In `do-while`, the condition is checked after execution.

---

## 11. What is an infinite loop?

**Answer:**
An infinite loop is a loop that never ends because its condition always remains true.

Example:

```c
while(1) {
    printf("Hello");
}
```

---

## 12. What is the use of `break` in a loop?

**Answer:**
`break` immediately terminates the loop.

---

## 13. What is the use of `continue` in a loop?

**Answer:**
`continue` skips the rest of the current iteration and moves to the next iteration.

---

## 14. Write a program to print numbers from 1 to 5 using a `for` loop.

**Answer:**

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

---

## 15. Write a program to print numbers from 1 to 5 using a `while` loop.

**Answer:**

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

---

## 16. Write a program to print numbers from 1 to 5 using a `do-while` loop.

**Answer:**

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

---

## 17. Write a program to find the sum of first 10 natural numbers.

**Answer:**

```c
#include <stdio.h>

int main() {
    int i, sum = 0;
    for (i = 1; i <= 10; i++) {
        sum = sum + i;
    }
    printf("Sum = %d", sum);
    return 0;
}
```

---

## 18. Write a program to print the multiplication table of a number.

**Answer:**

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

---

## 19. What is a nested loop?

**Answer:**
A nested loop is a loop inside another loop.

---

## 20. Where are loops useful in real programs?

**Answer:**
Loops are useful in counting, summing, printing patterns, processing arrays, searching, sorting, and repeated input/output.

---

# 4. Arrays

## 1. What is an array?

**Answer:**
An array is a collection of elements of the same data type stored in contiguous memory locations.

---

## 2. Why are arrays used?

**Answer:**
Arrays are used to store multiple values of the same type using a single variable name.

---

## 3. How do you declare an array in C?

**Answer:**
Syntax:

```c
data_type array_name[size];
```

Example:

```c
int marks[5];
```

---

## 4. What is array indexing?

**Answer:**
Array indexing means accessing array elements by position. In C, indexing starts from 0.

---

## 5. What is the first index of an array in C?

**Answer:**
The first index is `0`.

---

## 6. How do you access the third element of an array named `a`?

**Answer:**
The third element is accessed by:

```c
a[2]
```

---

## 7. What is meant by contiguous memory?

**Answer:**
Contiguous memory means all array elements are stored next to each other in adjacent memory locations.

---

## 8. Write a program to input 5 numbers into an array and print them.

**Answer:**

```c
#include <stdio.h>

int main() {
    int a[5], i;

    for (i = 0; i < 5; i++) {
        scanf("%d", &a[i]);
    }

    for (i = 0; i < 5; i++) {
        printf("%d ", a[i]);
    }

    return 0;
}
```

---

## 9. Write a program to find the sum of array elements.

**Answer:**

```c
#include <stdio.h>

int main() {
    int a[5], i, sum = 0;

    for (i = 0; i < 5; i++) {
        scanf("%d", &a[i]);
        sum += a[i];
    }

    printf("Sum = %d", sum);
    return 0;
}
```

---

## 10. How do you find the largest element in an array?

**Answer:**
Compare all elements one by one and keep track of the maximum value.

---

## 11. Write a program to find the largest element in an array.

**Answer:**

```c
#include <stdio.h>

int main() {
    int a[5], i, max;

    for (i = 0; i < 5; i++) {
        scanf("%d", &a[i]);
    }

    max = a[0];

    for (i = 1; i < 5; i++) {
        if (a[i] > max) {
            max = a[i];
        }
    }

    printf("Largest = %d", max);
    return 0;
}
```

---

## 12. What is linear search?

**Answer:**
Linear search is a method of finding an element by checking each array element one by one from the beginning.

---

## 13. What is sorting?

**Answer:**
Sorting is the process of arranging data in ascending or descending order.

---

## 14. Name two common sorting orders.

**Answer:**

* Ascending order
* Descending order

---

## 15. Write a program to reverse an array.

**Answer:**

```c
#include <stdio.h>

int main() {
    int a[5], i;

    for (i = 0; i < 5; i++) {
        scanf("%d", &a[i]);
    }

    for (i = 4; i >= 0; i--) {
        printf("%d ", a[i]);
    }

    return 0;
}
```

---

## 16. What is a two-dimensional array?

**Answer:**
A two-dimensional array is an array of arrays. It is used to store data in rows and columns.

Example:

```c
int a[3][4];
```

---

## 17. What is the use of a two-dimensional array?

**Answer:**
It is used for tables, matrices, and grid-like data.

---

## 18. What is an array of strings?

**Answer:**
An array of strings is a collection of multiple strings stored together.

Example:

```c
char names[3][20];
```

---

## 19. Can an array store different data types?

**Answer:**
No. A single array stores elements of only one data type.

---

## 20. What are the advantages of arrays?

**Answer:**
Arrays make it easy to:

* store many values
* process data with loops
* search and sort data
* reduce code repetition

---

# 5. Characters and Strings

## 1. What is a character in C?

**Answer:**
A character is a single symbol stored in a variable of type `char`.

Example:

```c
char ch = 'A';
```

---

## 2. What is a string in C?

**Answer:**
A string is a sequence of characters terminated by the null character `'\0'`.

---

## 3. How are strings stored in C?

**Answer:**
Strings are stored as character arrays.

Example:

```c
char name[20];
```

---

## 4. What is the null character?

**Answer:**
The null character `'\0'` marks the end of a string in C.

---

## 5. What is the difference between a character and a string?

**Answer:**
A character stores one symbol, while a string stores a sequence of characters.

Example:

```c
char ch = 'A';
char str[] = "A";
```

---

## 6. How do you input a string in C?

**Answer:**
A string can be input using `scanf("%s", str);` or `gets()` in older code, though `fgets()` is safer.

---

## 7. How do you print a string in C?

**Answer:**
A string can be printed using:

```c
printf("%s", str);
```

---

## 8. What is string manipulation?

**Answer:**
String manipulation means performing operations on strings such as copying, comparing, joining, and finding length.

---

## 9. Name some common string functions in C.

**Answer:**
Common string functions are:

* `strlen()`
* `strcpy()`
* `strcat()`
* `strcmp()`

---

## 10. What does `strlen()` do?

**Answer:**
`strlen()` returns the length of a string excluding the null character.

---

## 11. What does `strcpy()` do?

**Answer:**
`strcpy()` copies one string into another.

---

## 12. What does `strcat()` do?

**Answer:**
`strcat()` joins one string to the end of another string.

---

## 13. What does `strcmp()` do?

**Answer:**
`strcmp()` compares two strings.

* returns `0` if equal
* negative if first is smaller
* positive if first is greater

---

## 14. Write a program to find the length of a string.

**Answer:**

```c
#include <stdio.h>
#include <string.h>

int main() {
    char str[100];
    scanf("%s", str);
    printf("Length = %d", strlen(str));
    return 0;
}
```

---

## 15. Write a program to copy one string to another.

**Answer:**

```c
#include <stdio.h>
#include <string.h>

int main() {
    char s1[100], s2[100];
    scanf("%s", s1);

    strcpy(s2, s1);

    printf("Copied string: %s", s2);
    return 0;
}
```

---

## 16. Write a program to concatenate two strings.

**Answer:**

```c
#include <stdio.h>
#include <string.h>

int main() {
    char s1[100], s2[100];
    scanf("%s %s", s1, s2);

    strcat(s1, s2);

    printf("Concatenated string: %s", s1);
    return 0;
}
```

---

## 17. Write a program to compare two strings.

**Answer:**

```c
#include <stdio.h>
#include <string.h>

int main() {
    char s1[100], s2[100];
    scanf("%s %s", s1, s2);

    if (strcmp(s1, s2) == 0)
        printf("Equal");
    else
        printf("Not Equal");

    return 0;
}
```

---

## 18. Can we access individual characters of a string?

**Answer:**
Yes. Since a string is a character array, individual characters can be accessed by index.

Example:

```c
str[0], str[1]
```

---

## 19. What is character handling?

**Answer:**
Character handling means reading, storing, checking, and manipulating individual characters.

---

## 20. What is the difference between `char name[] = "Hello";` and `char name[] = {'H','e','l','l','o','\0'};`?

**Answer:**
Both represent the same string. The first one uses string literal notation, and the second one uses explicit character array notation.
