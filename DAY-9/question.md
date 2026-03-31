# Chapter 5: Functions in C

## Written Question with Answers

<!-- **Each question carries 8 marks**

--- -->

## Question 1

**What is a function in C? Why are functions used in programming? Explain with examples.**

### Answer:

A **function** in C is a block of code that performs a specific task.
It helps divide a large program into smaller and manageable parts.

Functions are used in programming for the following reasons:

* to reduce code repetition
* to make programs easier to understand
* to improve readability
* to make debugging easier
* to reuse the same logic many times
* to divide a big problem into smaller parts

For example, if we need to add two numbers many times in a program, instead of writing the same code again and again, we can write a function once and call it whenever needed.

### Example:

```c
#include <stdio.h>

int add(int a, int b) {
    return a + b;
}

int main() {
    printf("%d\n", add(5, 7));
    return 0;
}
```

Here, `add()` is a function that adds two numbers.
So, functions make a program shorter, cleaner, and more organized.

---

## Question 2

**What is the difference between library functions and user-defined functions? Explain with examples.**

### Answer:

In C, functions are mainly of two types:

### 1. Library Functions

Library functions are predefined functions provided by the C language.
The programmer can use them directly by including the required header file.

Examples:

* `printf()`
* `scanf()`
* `sqrt()`
* `strlen()`

### 2. User-Defined Functions

User-defined functions are created by the programmer according to the need of the program.

Examples:

* `add()`
* `square()`
* `greet()`

### Differences:

* Library functions are already built-in, but user-defined functions are written by the programmer.
* Library functions usually require header files, but user-defined functions do not need library implementation.
* Library functions are general-purpose, while user-defined functions are problem-specific.

### Example of library function:

```c
printf("Hello");
```

### Example of user-defined function:

```c
int square(int x) {
    return x * x;
}
```

Therefore, library functions save time, while user-defined functions help solve specific problems.

---

## Question 3

**Explain the main components of a function in C.**

### Answer:

A function in C has three main components:

### 1. Function Definition

The function definition is the actual body of the function where the task is performed.

Example:

```c
int add(int a, int b) {
    return a + b;
}
```

### 2. Function Prototype

A function prototype tells the compiler in advance that a function exists.

Example:

```c
int add(int, int);
```

### 3. Function Arguments / Parameters

Parameters are variables written in the function definition.
Arguments are the actual values passed during function call.

Example:

```c
add(5, 7);
```

Here, `5` and `7` are arguments.

### Structure of a function:

```c
return_type function_name(parameter_list) {
    // statements
}
```

Example:

```c
int multiply(int x, int y) {
    return x * y;
}
```

So, the main components of a function are definition, prototype, and arguments/parameters.

---

## Question 4

**What is a function prototype? Why is it needed in C? Explain with an example.**

### Answer:

A **function prototype** is a declaration of a function before it is used in the program.
It tells the compiler the name of the function, its return type, and its parameters.

### Example:

```c
int add(int, int);
```

### Why is it needed?

A function prototype is needed when the function definition is written below `main()`.
Without a prototype, the compiler may not understand the function call correctly.

### Example:

```c
#include <stdio.h>

int add(int, int);

int main() {
    printf("%d\n", add(10, 20));
    return 0;
}

int add(int a, int b) {
    return a + b;
}
```

### Importance of prototype:

* informs the compiler about the function in advance
* prevents errors
* improves program organization
* helps type checking

So, a function prototype is necessary for proper compilation and clear program structure.

---

## Question 5

**What is the difference between arguments and parameters? Explain with an example.**

### Answer:

Arguments and parameters are related to passing data to a function, but they are not the same.

### Parameter

A **parameter** is a variable written in the function definition or function prototype.

Example:

```c
int add(int a, int b)
```

Here, `a` and `b` are parameters.

### Argument

An **argument** is the actual value passed to the function when it is called.

Example:

```c
add(5, 7);
```

Here, `5` and `7` are arguments.

### Difference:

* Parameter = placeholder
* Argument = actual value

### Full example:

```c
#include <stdio.h>

int add(int a, int b) {
    return a + b;
}

int main() {
    int result = add(5, 7);
    printf("%d\n", result);
    return 0;
}
```

In this program:

* `a` and `b` are parameters
* `5` and `7` are arguments

Thus, parameters receive values, and arguments provide values.

---

## Question 6

**Explain the difference between a function with return value and a function without return value.**

### Answer:

In C, a function may return a value or may not return any value.

### 1. Function with return value

A function with return value sends a result back to the calling function.

Example:

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

Here, `square()` returns an integer value.

### 2. Function without return value

A function without return value performs a task but does not return anything.
Such functions use the return type `void`.

Example:

```c
#include <stdio.h>

void message() {
    printf("Welcome\n");
}

int main() {
    message();
    return 0;
}
```

### Difference:

* Function with return value → returns a result
* Function without return value → only performs an action

Therefore, the choice depends on whether a result is needed from the function or not.

---

## Question 7

**What are header files in C? Explain some common header files used with functions.**

### Answer:

A **header file** in C contains declarations of library functions, macros, and other useful information.
Header files are included in a program using the `#include` directive.

### Common header files:

#### 1. `stdio.h`

Used for input and output functions
Examples:

* `printf()`
* `scanf()`

#### 2. `math.h`

Used for mathematical functions
Examples:

* `sqrt()`
* `pow()`

#### 3. `string.h`

Used for string functions
Examples:

* `strlen()`
* `strcpy()`
* `strcmp()`

#### 4. `stdlib.h`

Used for utility functions
Examples:

* `rand()`
* `malloc()`

### Example:

```c
#include <stdio.h>
#include <math.h>
#include <string.h>
#include <stdlib.h>
```

### Importance of header files:

* allow use of library functions
* help the compiler identify function declarations
* make programming easier and organized

Thus, header files are essential when using predefined functions in C.

---

## Question 8

**Explain random number generation in C with an example.**

### Answer:

Random number generation in C is mainly done using the `rand()` function.
This function is available in the `stdlib.h` header file.

### Example:

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int r = rand();
    printf("%d\n", r);
    return 0;
}
```

This prints a random integer.

### Limiting the range

If we want a smaller range, we can use the modulus operator `%`.

Example:

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int r = rand() % 100;
    printf("%d\n", r);
    return 0;
}
```

This gives a number between 0 and 99.

### Use of `srand()`

`rand()` often gives the same sequence each time the program runs.
To change this, `srand()` is used to set a seed.

So, random number generation is useful in games, simulations, and test data generation.

---

## Question 9

**What is call by value? Explain with a program.**

### Answer:

In **call by value**, a copy of the actual variable is passed to the function.
So, any change made inside the function does not affect the original variable.

### Example:

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

### Output:

```text
10
```

### Explanation:

Here, `a` has the value `10`.
When `change(a)` is called, only a copy of `a` is passed to the function.
Inside the function, `x` becomes `100`, but the original variable `a` remains unchanged.

### Main idea:

* copy of value is passed
* original variable does not change

Thus, call by value is simple and safe when we do not want to modify the original variable.

---

## Question 10

**What is call by reference? Explain with a program.**

### Answer:

In **call by reference**, the address of the variable is passed to the function.
So, the function can directly modify the original variable.

### Example:

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

### Output:

```text
100
```

### Explanation:

Here, `&a` sends the address of `a` to the function.
Inside the function, `*x = 100` changes the value stored at that address.
So the original variable `a` becomes `100`.

### Main idea:

* address is passed
* original variable changes
* pointer is used

Therefore, call by reference is useful when a function needs to modify the original value.

---

## Question 11

**How can arrays be passed to functions in C? Explain with an example.**

### Answer:

Arrays can be passed to functions by sending the array name.
Usually, the size of the array is also passed, because the function needs to know how many elements it has to process.

### Example:

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

### Explanation:

* `arr[]` receives the array
* `n` receives the size of the array
* the function prints all elements one by one

### Another use

Arrays can also be passed to functions for:

* finding sum
* finding maximum
* searching elements
* sorting elements

Thus, passing arrays to functions makes array processing easier and more modular.

---

## Question 12

**What is recursion? Explain recursion with a factorial example.**

### Answer:

**Recursion** is a process in which a function calls itself.
It is used to solve a problem by breaking it into smaller similar subproblems.

### Important parts of recursion:

* **Base case**
* **Recursive call**

### Example: factorial

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

### Explanation:

`fact(5)`
= `5 * fact(4)`
= `5 * 4 * fact(3)`
= `5 * 4 * 3 * fact(2)`
= `5 * 4 * 3 * 2 * fact(1)`
= `5 * 4 * 3 * 2 * 1 * fact(0)`
= `120`

### Base case:

```c
if(n == 0)
    return 1;
```

This stops the recursion.

### Importance:

Without the base case, the function will call itself forever.

So, recursion is useful for problems like factorial, Fibonacci series, and tree traversal.
<!-- 
---

# Best 5 Questions to Select for Exam

এই 12টা থেকে যদি তুমি balanced 5টা নিতে চাও, তাহলে এই set ভালো হবে:

1. **Question 1** – basic concept of function
2. **Question 2** – library vs user-defined
3. **Question 4** – function prototype
4. **Question 9** – call by value
5. **Question 12** – recursion

আর যদি একটু practical-oriented set চাও, তাহলে:

1. **Question 3**
2. **Question 5**
3. **Question 6**
4. **Question 10**
5. **Question 11**

---

# Exam Paper Style Version

```text
Chapter 5: Functions in C
Written Test
Answer any five questions.
Each question carries 8 marks.

1. What is a function in C? Why are functions used in programming? Explain with examples.
2. What is the difference between library functions and user-defined functions? Explain with examples.
3. Explain the main components of a function in C.
4. What is a function prototype? Why is it needed in C? Explain with an example.
5. What is the difference between arguments and parameters? Explain with an example.
6. Explain the difference between a function with return value and a function without return value.
7. What are header files in C? Explain some common header files used with functions.
8. Explain random number generation in C with an example.
9. What is call by value? Explain with a program.
10. What is call by reference? Explain with a program.
11. How can arrays be passed to functions in C? Explain with an example.
12. What is recursion? Explain recursion with a factorial example.
```

চাইলে আমি next message-এ এগুলোকে আরও **student-friendly short answer sheet** আকারে compact করে দিতে পারি। -->











































































































<!-- Of course — below are **30 direct questions and answers** from the **Functions in C** chapter.
I made them **short, clear, and MCQ-friendly**, so you can easily pick **10** from here and turn them into MCQs.

---

# Functions in C -->

## Direct Questions and Answers

### 1. What is a function in C?

**Answer:** A function is a block of code that performs a specific task.

---

### 2. Why are functions used in C?

**Answer:** Functions are used to reduce code repetition and make programs modular.

---

### 3. What is a library function?

**Answer:** A library function is a predefined function provided by C.

---

### 4. What is a user-defined function?

**Answer:** A user-defined function is a function created by the programmer.

---

### 5. Give one example of a library function.

**Answer:** `printf()`

---

### 6. Give one example of a user-defined function.

**Answer:** `add()`

---

### 7. What is a function prototype?

**Answer:** A function prototype is a declaration of a function before it is used.

---

### 8. Why is a function prototype needed?

**Answer:** It tells the compiler about the function before its actual definition.

---

### 9. What is a function definition?

**Answer:** A function definition is the actual body of the function where the work is done.

---

### 10. What is a function call?

**Answer:** A function call is the statement that executes a function.

---

### 11. What is a parameter?

**Answer:** A parameter is a variable written in a function definition.

---

### 12. What is an argument?

**Answer:** An argument is the actual value passed to a function during a function call.

---

### 13. What is the difference between parameter and argument?

**Answer:** A parameter is a placeholder, while an argument is the actual value.

---

### 14. What is the return type of a function?

**Answer:** The return type specifies the type of value a function returns.

---

### 15. What does `void` mean in a function?

**Answer:** `void` means the function does not return any value.

---

### 16. What is a header file in C?

**Answer:** A header file contains declarations of library functions.

---

### 17. Which header file is used for `printf()` and `scanf()`?

**Answer:** `stdio.h`

---

### 18. Which header file is used for `sqrt()`?

**Answer:** `math.h`

---

### 19. Which header file is used for `strlen()`?

**Answer:** `string.h`

---

### 20. Which header file is used for `rand()`?

**Answer:** `stdlib.h`

---

### 21. What is `rand()` used for?

**Answer:** `rand()` is used to generate random numbers.

---

### 22. What is `srand()` used for?

**Answer:** `srand()` is used to set the seed for random number generation.

---

### 23. What is call by value?

**Answer:** In call by value, a copy of the variable is passed to the function.

---

### 24. Does the original variable change in call by value?

**Answer:** No, the original variable does not change.

---

### 25. What is call by reference?

**Answer:** In call by reference, the address of the variable is passed to the function.

---

### 26. Does the original variable change in call by reference?

**Answer:** Yes, the original variable can change.

---

### 27. What is passed in call by reference?

**Answer:** The address of the variable is passed.

---

### 28. Can arrays be passed to functions in C?

**Answer:** Yes, arrays can be passed to functions.

---

### 29. What is recursion?

**Answer:** Recursion is a process where a function calls itself.

---

### 30. What is a base case in recursion?

**Answer:** A base case is the condition that stops the recursive calls.

<!-- ---

# Very Short MCQ-Making Version

```text
1. What is a function in C?
Answer: A block of code that performs a specific task.

2. Why are functions used in C?
Answer: To reduce code repetition and make programs modular.

3. What is a library function?
Answer: A predefined function provided by C.

4. What is a user-defined function?
Answer: A function created by the programmer.

5. Give one example of a library function.
Answer: printf()

6. Give one example of a user-defined function.
Answer: add()

7. What is a function prototype?
Answer: A declaration of a function before it is used.

8. Why is a function prototype needed?
Answer: It tells the compiler about the function before its definition.

9. What is a function definition?
Answer: The actual body of the function where the work is done.

10. What is a function call?
Answer: The statement that executes a function.

11. What is a parameter?
Answer: A variable written in a function definition.

12. What is an argument?
Answer: The actual value passed to a function during a function call.

13. What is the difference between parameter and argument?
Answer: Parameter is a placeholder, argument is the actual value.

14. What is the return type of a function?
Answer: It specifies the type of value a function returns.

15. What does void mean in a function?
Answer: The function does not return any value.

16. What is a header file in C?
Answer: A file containing declarations of library functions.

17. Which header file is used for printf() and scanf()?
Answer: stdio.h

18. Which header file is used for sqrt()?
Answer: math.h

19. Which header file is used for strlen()?
Answer: string.h

20. Which header file is used for rand()?
Answer: stdlib.h

21. What is rand() used for?
Answer: To generate random numbers.

22. What is srand() used for?
Answer: To set the seed for random numbers.

23. What is call by value?
Answer: Passing a copy of the variable.

24. Does the original variable change in call by value?
Answer: No.

25. What is call by reference?
Answer: Passing the address of the variable.

26. Does the original variable change in call by reference?
Answer: Yes.

27. What is passed in call by reference?
Answer: The address of the variable.

28. Can arrays be passed to functions in C?
Answer: Yes.

29. What is recursion?
Answer: A function calling itself.

30. What is a base case in recursion?
Answer: The condition that stops recursion.
```

চাইলে আমি এখন এগুলো থেকে **ready-made 10 MCQ with options and answers** বানিয়ে দিই।
 -->
