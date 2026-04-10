# Chapter 5: Functions in C

## ICT 1101 – Structured Programming Language

---

## 1. Introduction

A **function** is a block of code that performs a specific task.

In C programming, functions are used to divide a large program into smaller and manageable parts.
Instead of writing the same code again and again, we can write it once inside a function and use it whenever needed.

### Example

A function can be used to:

* add two numbers
* find the maximum number
* print a message
* calculate factorial

---

## 2. Why Do We Use Functions?

Functions are used for the following reasons:

* to reduce code repetition
* to make the program shorter
* to make the program easier to read
* to make debugging easier
* to make the program reusable
* to divide a big problem into smaller parts

### Simple idea

Without function:

* same code must be written many times

With function:

* write once, use many times

---

## 3. General Structure of a Function

```c
return_type function_name(parameter_list) {
    // function body
}
```

### Explanation

* **return_type** → the type of value returned by the function
* **function_name** → the name of the function
* **parameter_list** → values received by the function
* **function body** → the statements that do the কাজ

---

## 4. Types of Functions

There are two main types of functions in C:

### 4.1 Library Functions

These are predefined functions provided by C.

Examples:

* `printf()`
* `scanf()`
* `sqrt()`
* `strlen()`
* `rand()`

### 4.2 User Defined Functions

These are functions created by the programmer according to the need of the program.

Examples:

* `add()`
* `largest()`
* `greet()`
* `factorial()`

---

# 5. Library Functions

Library functions are already available in C libraries.
We only need to include the correct header file to use them.

### Examples

| Function   | Purpose                | Header File |
| ---------- | ---------------------- | ----------- |
| `printf()` | display output         | `stdio.h`   |
| `scanf()`  | take input             | `stdio.h`   |
| `sqrt()`   | find square root       | `math.h`    |
| `strlen()` | find string length     | `string.h`  |
| `rand()`   | generate random number | `stdlib.h`  |

### Example

```c
#include <stdio.h>
#include <math.h>

int main() {
    printf("%.2f\n", sqrt(25));
    return 0;
}
```

---

# 6. User Defined Functions

User defined functions are created by the programmer.

### Example

```c
#include <stdio.h>

void greet() {
    printf("Welcome to C Functions\n");
}

int main() {
    greet();
    return 0;
}
```

### Explanation

Here:

* `greet()` is a user defined function
* it does not return any value, so return type is `void`
* it is called from `main()`

---

# 7. Function Components

A function has three important components:

* Function Definition
* Function Prototype
* Function Arguments / Parameters

---

## 7.1 Function Definition

The **function definition** is the actual body of the function where the work is done.

### Example

```c
int add(int a, int b) {
    return a + b;
}
```

### Explanation

* `int` → return type
* `add` → function name
* `int a, int b` → parameters
* `return a + b;` → returns the result

---

## 7.2 Function Prototype

A **function prototype** tells the compiler that a function exists before it is used.

### Example

```c
#include <stdio.h>

int add(int, int);   // prototype

int main() {
    printf("%d\n", add(5, 7));
    return 0;
}

int add(int a, int b) {
    return a + b;
}
```

### Why do we need it?

If the function definition is written below `main()`, then a prototype is needed above `main()`.

---

## 7.3 Function Arguments and Parameters

### Parameter

A **parameter** is a variable written in the function definition.

### Argument

An **argument** is the actual value passed to the function when it is called.

### Example

```c
int add(int a, int b)
```

Here, `a` and `b` are parameters.

```c
add(5, 7);
```

Here, `5` and `7` are arguments.

### Easy rule

* **Parameter = placeholder**
* **Argument = actual value**

---

# 8. Function Call

A function is executed by calling it.

### Example

```c
#include <stdio.h>

void hello() {
    printf("Hello Student\n");
}

int main() {
    hello();
    return 0;
}
```

### How it works

1. `main()` starts execution
2. `hello()` is called
3. control goes to `hello()`
4. after execution, control returns to `main()`

---

# 9. Return Type of a Function

A function may or may not return a value.

### 9.1 Function with return value

```c
#include <stdio.h>

int square(int x) {
    return x * x;
}

int main() {
    int result = square(5);
    printf("%d\n", result);
    return 0;
}
```

### 9.2 Function without return value

```c
#include <stdio.h>

void message() {
    printf("This function returns nothing\n");
}

int main() {
    message();
    return 0;
}
```

### Important

* `int`, `float`, `char` → used when function returns a value
* `void` → used when function returns nothing

---

# 10. Header Files

A **header file** contains declarations of library functions.

### Common Header Files

| Header File | Use                              |
| ----------- | -------------------------------- |
| `stdio.h`   | input/output                     |
| `math.h`    | mathematical functions           |
| `string.h`  | string functions                 |
| `stdlib.h`  | random numbers, memory functions |

### Example

```c
#include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>
```

---

# 11. Random Number Generation

Random numbers are generated using `rand()`.

### Example

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int r = rand();
    printf("%d\n", r);
    return 0;
}
```

### To limit the range

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int r = rand() % 100;
    printf("%d\n", r);
    return 0;
}
```

### Explanation

* `rand()` gives a random integer
* `rand() % 100` gives a number between `0` and `99`

---

# 12. Parameter Passing

There are two common ways of passing data to a function:

* Call by Value
* Call by Reference

---

## 12.1 Call by Value

In **call by value**, a copy of the variable is passed to the function.

So, the original variable does not change.

### Example

```c
#include <stdio.h>

void change(int x) {
    x = 100;
}

int main() {
    int a = 10;
    change(a);
    printf("%d\n", a);
    return 0;
}
```

### Output

```c
10
```

### Explanation

The original variable `a` remains unchanged because only a copy of `a` is passed.

---

## 12.2 Call by Reference

In **call by reference**, the address of the variable is passed to the function.

So, the original variable can be changed.

### Example

```c
#include <stdio.h>

void change(int *x) {
    *x = 100;
}

int main() {
    int a = 10;
    change(&a);
    printf("%d\n", a);
    return 0;
}
```

### Output

```c
100
```

### Explanation

The function receives the address of `a`, so it can directly modify the original value.

---

# 13. Call by Value vs Call by Reference

| Topic                      | Call by Value | Call by Reference   |
| -------------------------- | ------------- | ------------------- |
| What is passed?            | Copy of value | Address of variable |
| Original variable changes? | No            | Yes                 |
| Easier to understand?      | Yes           | Slightly tricky     |
| Uses pointer?              | No            | Yes                 |

---

# 14. Passing Arrays to Functions

Arrays can also be passed to functions.

### Example: print array elements

```c
#include <stdio.h>

void printArray(int arr[], int n) {
    int i;
    for(i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
}

int main() {
    int a[5] = {10, 20, 30, 40, 50};
    printArray(a, 5);
    return 0;
}
```

### Explanation

* `arr[]` receives the array
* `n` tells the function the size of the array

### Example: sum of array

```c
#include <stdio.h>

int sumArray(int arr[], int n) {
    int i, sum = 0;
    for(i = 0; i < n; i++) {
        sum += arr[i];
    }
    return sum;
}

int main() {
    int a[5] = {1, 2, 3, 4, 5};
    printf("%d\n", sumArray(a, 5));
    return 0;
}
```

---

# 15. Recursion

**Recursion** is a process where a function calls itself.

### Important parts of recursion

* **Base case**
* **Recursive call**

### Example: Factorial

```c
#include <stdio.h>

int fact(int n) {
    if(n == 0)
        return 1;
    else
        return n * fact(n - 1);
}

int main() {
    printf("%d\n", fact(5));
    return 0;
}
```

### Explanation

`fact(5)`
= `5 * fact(4)`
= `5 * 4 * fact(3)`
= `5 * 4 * 3 * fact(2)`
= `5 * 4 * 3 * 2 * fact(1)`
= `5 * 4 * 3 * 2 * 1 * fact(0)`
= `120`

### Base case

```c
if(n == 0)
    return 1;
```

### Why is base case important?

Without the base case, the function will call itself forever.

---

# 16. Full Example Program

```c
#include <stdio.h>

int add(int a, int b);      // prototype
void message();             // prototype

void message() {
    printf("Functions are important in C\n");
}

int add(int a, int b) {
    return a + b;
}

int main() {
    int x = 10, y = 20, result;
    
    message();
    result = add(x, y);
    
    printf("Sum = %d\n", result);
    return 0;
}
```

### This program shows

* prototype
* user defined function
* function call
* return value
* parameter passing

---

# 17. Common Mistakes

Students often make these mistakes:

### 1. Forgetting semicolon after prototype

Wrong:

```c
int add(int, int)
```

Correct:

```c
int add(int, int);
```

### 2. Confusing parameter and argument

* parameter → written in definition
* argument → passed in call

### 3. Wrong return type

If a function is `int`, it must return an integer value.

### 4. Forgetting header file

Using `strlen()` without `#include <string.h>`

### 5. Forgetting base case in recursion

This causes infinite recursion.

### 6. Not passing array size

Without size, function cannot know how many elements to process.

---

# 18. Short Summary

## Main Points to Remember

* A function is a block of code that performs a specific task.
* Functions make programs modular and reusable.
* There are two types of functions:

  * library functions
  * user-defined functions
* Function components:

  * definition
  * prototype
  * arguments/parameters
* Functions may return a value or may return nothing.
* Data can be passed by value or by reference.
* Arrays can be passed to functions.
* Recursion means a function calling itself.

---

# 19. Important Definitions

### Function

A block of code that performs a specific task.

### Library Function

A predefined function provided by C.

### User Defined Function

A function created by the programmer.

### Function Prototype

A declaration of a function before its use.

### Parameter

A variable written in a function definition.

### Argument

An actual value passed to a function.

### Call by Value

Passing a copy of a variable.

### Call by Reference

Passing the address of a variable.

### Recursion

A function calling itself.

---

# 20. Practice Questions

## Short Questions

1. What is a function?
2. Why do we use functions?
3. What is a library function?
4. What is a user-defined function?
5. What is a function prototype?
6. What is the difference between parameter and argument?
7. What is call by value?
8. What is call by reference?
9. What is recursion?
10. Why is base case important in recursion?

## Descriptive Questions

1. Explain the advantages of using functions in C.
2. Differentiate between library functions and user-defined functions.
3. Explain function definition, function prototype, and function arguments.
4. Compare call by value and call by reference.
5. Explain recursion with an example.

## Programming Questions

1. Write a function to add two numbers.
2. Write a function to find the square of a number.
3. Write a function to print a message.
4. Write a program to find the sum of array elements using a function.
5. Write a recursive function to calculate factorial.

---

# 21. Quick Revision Box

```text
Function → a block of code for a specific task
Library function → built-in
User-defined function → created by programmer
Prototype → declaration before use
Parameter → placeholder
Argument → actual value
Call by value → copy is passed
Call by reference → address is passed
Recursion → function calls itself
```
