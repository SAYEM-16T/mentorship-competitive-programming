# Memory and Program Execution

## Student-Friendly Notes / Handout

## Introduction

When we run a program on a computer, the program needs a place to store instructions, numbers, variables, and results. That place is called **memory**.

The **CPU** (Central Processing Unit) works with memory to run the program. It reads data from memory, processes it, and writes the result back to memory.

To understand this process, we need to learn four important ideas:

1. **Memory Organization**
2. **Memory Access**
3. **Number Representation**
4. **Memory Addressing**

---

# 1. Memory Organization

## How programs and data are stored in computer memory

### What is memory?

Computer memory can be thought of as a large collection of small storage locations. Each location can hold data.

When a program runs, memory stores:

* Program instructions
* Input data
* Variables
* Temporary results
* Final output

### Simple idea

You can imagine memory as a large shelf with many boxes.
Each box can store some information.

For example, in this code:

```c
int a = 5;
int b = 10;
int sum = a + b;
```

The computer stores:

* `a` in memory
* `b` in memory
* `sum` in memory

The values `5`, `10`, and later `15` are placed into those memory locations.

### Different parts of memory

At a basic level, memory may be divided into different areas:

* **Code section** → stores program instructions
* **Data section** → stores fixed or global data
* **Stack** → stores local variables and function calls
* **Heap** → stores dynamically allocated memory

For beginners, it is enough to understand this:

> A running program stores different kinds of information in different parts of memory.

### Why is memory organization important?

It helps us understand:

* where variables are stored
* how programs run
* how memory is used efficiently
* why some programming errors happen

---

# 2. Memory Access

## How the CPU reads and writes data in memory

### Main idea

The CPU does not do everything by itself.
It needs to get data from memory.

The CPU mainly performs two actions:

* **Read** → take data from memory
* **Write** → put data into memory

### Read operation

When the CPU takes data from memory, it is called **reading**.

Example:

```c
int x = 7;
int y = x + 2;
```

Here, the CPU reads the value of `x` from memory.

### Write operation

When the CPU stores data into memory, it is called **writing**.

In the same example:

* `x = 7` means `7` is written into memory
* `y = x + 2` means the result is written into memory

### How the CPU accesses memory

The CPU usually works like this:

1. Find where the data is located
2. Read the data from memory
3. Process the data
4. Write the result back to memory

### Registers

The CPU also uses very small and very fast storage areas called **registers**.

A simple flow is:

**Memory → Register → CPU processes → Memory**

You can explain it like this:

* **Memory** is like a store room
* **Register** is like a small desk near the worker
* The CPU takes data from memory, uses it on the desk, then stores the result back

### Example

```c
int a = 4;
int b = 6;
int c = a + b;
```

What happens?

* CPU reads `a`
* CPU reads `b`
* CPU adds them
* CPU writes the result into `c`

### Why memory access matters

It helps students understand:

* how a program executes step by step
* how data moves inside a computer
* why memory speed affects performance

---

# 3. Number Representation

## How numbers are stored in memory

Computers store all data in **binary** form.

Even if we write numbers in decimal, the computer changes them into binary before storing them.

This section has three parts:

* Decimal numbers
* Binary numbers
* Floating-point numbers

---

## 3.1 Decimal Numbers

### What is decimal?

Decimal is the number system we use in daily life.

It uses 10 digits:

`0, 1, 2, 3, 4, 5, 6, 7, 8, 9`

So, decimal is called a **base-10** number system.

### Example

The decimal number `345` means:

* 3 × 10²
* 4 × 10¹
* 5 × 10⁰

So:

`345 = 300 + 40 + 5`

### Why learn decimal first?

Because students already know decimal numbers.
It helps them understand how other number systems work.

---

## 3.2 Binary Numbers

### What is binary?

Binary is the number system used by computers.

It uses only 2 digits:

`0` and `1`

So, binary is a **base-2** number system.

### Example

Binary number:

`1011₂`

This means:

* 1 × 2³ = 8
* 0 × 2² = 0
* 1 × 2¹ = 2
* 1 × 2⁰ = 1

So:

`1011₂ = 11₁₀`

### Why do computers use binary?

Because computer hardware works well with two states:

* ON / OFF
* High / Low
* 1 / 0

### Bit and byte

* **Bit** = one binary digit (`0` or `1`)
* **Byte** = 8 bits

Example:

`00000101` = decimal `5`

### Signed and unsigned numbers

* **Unsigned number** → only positive values and zero
* **Signed number** → can represent positive and negative values

For example:

* 8-bit unsigned range: `0 to 255`
* 8-bit signed range: `-128 to 127`

For beginners, it is enough to say:

> Computers use special methods to store negative numbers in binary.

---

## 3.3 Floating-Point Numbers

### What are floating-point numbers?

Floating-point numbers are used to store numbers with fractions or decimal points.

Examples:

* 3.14
* 0.5
* -12.75

### Why are they different?

Integer numbers such as `5` or `10` are simple to store.

But numbers like `3.14` need a special format because the decimal point must also be represented.

### Simple idea

Floating-point numbers are stored in a form similar to scientific notation.

For example:

`4500 = 4.5 × 10³`

A floating-point number usually has:

* **Sign** → positive or negative
* **Exponent** → where the decimal point moves
* **Mantissa / Significand** → the main digits

### Important note

Floating-point numbers are not always exact.

For example, in some programming languages:

```python
0.1 + 0.2
```

may not give exactly `0.3`.

This happens because some decimal numbers cannot be stored perfectly in binary floating-point form.

### Why floating-point is important

It helps students understand:

* rounding errors
* approximation in computers
* why decimal calculations can sometimes be slightly inaccurate

---

# 4. Memory Addressing

## Understanding addresses and how variables are located in memory

### What is an address?

Each memory location has a unique number.
This number is called its **address**.

An address tells the computer where data is stored.

### Simple example

Imagine memory like houses on a street.

Each house has:

* a house number
* something stored inside

In memory:

* Address `1000` → value `5`
* Address `1004` → value `10`
* Address `1008` → value `15`

### Variables and addresses

When we write:

```c
int x = 5;
```

we use the name `x`.

But the computer does not really think in names.
It uses the memory address where `x` is stored.

So:

* Humans use the name `x`
* The computer uses the address of `x`

### Why are addresses needed?

The CPU must know where data is stored.
Without an address, it cannot find or use the value.

### Example

```c
int a = 20;
```

Suppose `a` is stored at address `2000`.

That means:

* variable name: `a`
* memory address: `2000`
* value stored there: `20`

When the CPU needs `a`, it reads the value from address `2000`.

### Variable size and address movement

Different data types use different amounts of memory.

Examples:

* `char` → 1 byte
* `int` → 4 bytes
* `double` → 8 bytes

So if one `int` starts at address `1000`, the next `int` may start at `1004`.

That is because the first integer uses 4 bytes.

### Connection to pointers

Memory addressing is the foundation of **pointers**.

A pointer is simply a variable that stores a memory address.

Students do not need full pointer details yet, but it is good to mention:

> A pointer stores the address of another variable.

---

# How All Topics Work Together

Consider this program:

```c
int a = 5;
int b = 10;
int c = a + b;
```

Now let us connect all four topics.

## Memory Organization

The variables `a`, `b`, and `c` are stored in memory.

## Memory Addressing

Each variable has its own address.

## Memory Access

The CPU reads the values of `a` and `b`, adds them, and writes the result into `c`.

## Number Representation

Although we write `5`, `10`, and `15` in decimal, the computer stores them in binary.

---

# Easy Real-Life Comparisons

## Memory Organization

Memory is like a cupboard with many drawers.

## Memory Access

The CPU is like a person opening a drawer, taking something out, using it, and putting it back.

## Number Representation

Humans usually count in base 10, but computers count in base 2.

## Memory Addressing

A memory address is like a house address or a seat number. It tells us exactly where something is.

---

# Common Student Confusions

## 1. Variable name vs memory address

Students often think the name `x` is what the computer uses directly.
Actually, the computer uses the address of `x`.

## 2. Decimal vs binary

Students may think computers store decimal numbers directly.
In reality, computers store data in binary.

## 3. Floating-point accuracy

Students may think `0.1` is always stored exactly.
But floating-point values are often approximations.

## 4. CPU and memory

Students may think the CPU already has all data inside it.
Actually, it must read data from memory and then write results back.

---

# Quick Summary

## Memory Organization

It explains how programs and data are arranged in memory.

## Memory Access

It explains how the CPU reads data from memory and writes data back.

## Number Representation

It explains how numbers are stored in binary form inside the computer.

## Memory Addressing

It explains how each data item is located by a unique memory address.

---

# Short Conclusion

When a program runs, its instructions and data are stored in memory.
Each piece of data has a memory address.
The CPU uses these addresses to read and write data.
Although humans use decimal numbers, computers store numbers in binary.
For fractional numbers, computers use floating-point representation.

Understanding these ideas is the first step toward learning how programs really work inside a computer.

---

# Mini Practice Questions

1. What is computer memory?
2. What does the CPU do when it reads data from memory?
3. Why do computers use binary numbers?
4. What is the difference between decimal and binary?
5. What is a memory address?
6. Why are floating-point numbers sometimes not exact?
7. What is the difference between reading and writing in memory?

---

# One-Line Revision Notes

* **Memory** stores program instructions and data.
* **CPU** reads from memory, processes data, and writes results back.
* **Binary** is the language of computer memory.
* **Address** tells where data is stored.
* **Floating-point** is used for numbers with fractions.

---
---
---
---
---
---
---
---



# Dynamic Memory Allocation in C

## `malloc()`, `calloc()`, `realloc()`, and `free()`

## 1. Introduction

In C programming, memory can be allocated in two ways:

### A. Static Memory Allocation

Memory size is fixed before the program runs.

Example:

```c
int x;
int arr[5];
```

Here:

* `x` always uses memory for one integer
* `arr` always uses memory for 5 integers

This is simple, but not flexible.

---

### B. Dynamic Memory Allocation

Memory is allocated **during program execution**.

This is useful when:

* the number of values is not known in advance
* memory needs to grow or shrink later
* the program needs flexibility

To do dynamic memory allocation in C, we use functions from the `stdlib.h` library:

```c
#include <stdlib.h>
```

The main functions are:

* `malloc()`
* `calloc()`
* `realloc()`
* `free()`

---

# 2. `malloc()`

## Definition

`malloc()` stands for **memory allocation**.

It allocates a block of memory of the requested size and returns the address of the first byte of that memory.

### Important:

`malloc()` **does not initialize** the memory.
So, the memory may contain **garbage values**.

---

## Syntax

```c
pointer = (type *) malloc(size_in_bytes);
```

---

## Example 1: Allocate memory for one integer

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *p;

    p = (int *) malloc(sizeof(int));

    *p = 25;

    printf("Value = %d\n", *p);

    free(p);
    return 0;
}
```

---

## Explanation

* `malloc(sizeof(int))` allocates memory for one integer
* `p` stores the address of that memory
* `*p = 25` stores the value `25` in that memory location
* `free(p)` releases the memory after use

---

## Example 2: Allocate memory for an array

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *arr;
    int n = 5;

    arr = (int *) malloc(n * sizeof(int));

    for (int i = 0; i < n; i++) {
        arr[i] = (i + 1) * 10;
    }

    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }

    free(arr);
    return 0;
}
```

### Output

```c
10 20 30 40 50
```

---

## Key Point

If you use `malloc()`, the allocated memory is **not automatically set to zero**.

So this:

```c
int *arr = (int *) malloc(5 * sizeof(int));
```

does **not** guarantee that `arr[0]`, `arr[1]`, etc. will contain `0`.

---

# 3. `calloc()`

## Definition

`calloc()` stands for **contiguous allocation**.

It allocates memory for multiple elements and **initializes all bytes to zero**.

---

## Syntax

```c
pointer = (type *) calloc(number_of_elements, size_of_each_element);
```

---

## Example

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *arr;
    int n = 5;

    arr = (int *) calloc(n, sizeof(int));

    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }

    free(arr);
    return 0;
}
```

### Output

```c
0 0 0 0 0
```

---

## Explanation

* `calloc(5, sizeof(int))` allocates memory for 5 integers
* all elements are initialized to `0`

---

# 4. Difference Between `malloc()` and `calloc()`

| Feature             | `malloc()`                 | `calloc()`                                           |
| ------------------- | -------------------------- | ---------------------------------------------------- |
| Full form           | Memory Allocation          | Contiguous Allocation                                |
| Number of arguments | 1                          | 2                                                    |
| Initialization      | Does not initialize memory | Initializes memory to zero                           |
| Speed               | Usually slightly faster    | May be slightly slower because it initializes memory |

---

## Simple Comparison

```c
int *a = (int *) malloc(5 * sizeof(int));
int *b = (int *) calloc(5, sizeof(int));
```

* `a` may contain garbage values
* `b` will contain all zeros

---

# 5. `realloc()`

## Definition

`realloc()` stands for **re-allocation**.

It changes the size of previously allocated memory.

You can use it to:

* increase memory size
* decrease memory size

---

## Syntax

```c
pointer = (type *) realloc(pointer, new_size_in_bytes);
```

---

## Example

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *arr;

    arr = (int *) malloc(3 * sizeof(int));

    arr[0] = 10;
    arr[1] = 20;
    arr[2] = 30;

    arr = (int *) realloc(arr, 6 * sizeof(int));

    arr[3] = 40;
    arr[4] = 50;
    arr[5] = 60;

    for (int i = 0; i < 6; i++) {
        printf("%d ", arr[i]);
    }

    free(arr);
    return 0;
}
```

### Output

```c
10 20 30 40 50 60
```

---

## Explanation

* first, memory is allocated for 3 integers
* later, memory is expanded to hold 6 integers
* old values remain available if reallocation is successful
* new positions can be used to store more values

---

## Important Note

`realloc()` may:

* extend the same memory block, or
* allocate a new block and copy the old data

So the returned pointer may be different from the old one.

---

## Safer Version of `realloc()`

```c
int *temp = realloc(arr, 6 * sizeof(int));

if (temp != NULL) {
    arr = temp;
}
```

This is safer because if `realloc()` fails, it returns `NULL`, and the original pointer is not lost.

---

# 6. `free()`

## Definition

`free()` releases dynamically allocated memory back to the system.

If dynamically allocated memory is not freed, it causes a **memory leak**.

---

## Syntax

```c
free(pointer);
```

---

## Example

```c
int *p = (int *) malloc(sizeof(int));
*p = 100;

free(p);
```

---

## Good Practice

After freeing memory, set the pointer to `NULL`.

```c
free(p);
p = NULL;
```

This helps avoid accidental use of a freed pointer.

---

# 7. Complete Example Using All Concepts

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *arr;
    int n = 3;

    arr = (int *) malloc(n * sizeof(int));

    arr[0] = 10;
    arr[1] = 20;
    arr[2] = 30;

    printf("After malloc:\n");
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }

    printf("\n");

    n = 5;
    arr = (int *) realloc(arr, n * sizeof(int));

    arr[3] = 40;
    arr[4] = 50;

    printf("After realloc:\n");
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }

    printf("\n");

    free(arr);
    arr = NULL;

    return 0;
}
```

---

# 8. Common Errors and Mistakes

## 1. Using memory without allocation

```c
int *p;
*p = 10;   // Wrong
```

Why wrong:

* `p` does not point to valid memory

---

## 2. Forgetting to free memory

```c
int *p = (int *) malloc(sizeof(int));
```

If `free(p);` is not used, memory remains occupied.

This is called a **memory leak**.

---

## 3. Using memory after `free()`

```c
free(p);
*p = 20;   // Wrong
```

Why wrong:

* the memory has already been released

This is dangerous.

---

## 4. Freeing the same pointer twice

```c
free(p);
free(p);   // Wrong
```

This may cause program crashes.

---

## 5. Not checking if allocation succeeded

Memory allocation may fail.

Better:

```c
int *p = (int *) malloc(5 * sizeof(int));

if (p == NULL) {
    printf("Memory allocation failed\n");
    return 1;
}
```

---

# 9. Summary Table

| Function    | Purpose                                | Initialization             | Example                          |
| ----------- | -------------------------------------- | -------------------------- | -------------------------------- |
| `malloc()`  | Allocates memory                       | No                         | `malloc(5 * sizeof(int))`        |
| `calloc()`  | Allocates memory for multiple elements | Yes, sets to 0             | `calloc(5, sizeof(int))`         |
| `realloc()` | Resizes allocated memory               | Keeps old data if possible | `realloc(ptr, 10 * sizeof(int))` |
| `free()`    | Releases allocated memory              | Not applicable             | `free(ptr)`                      |

---

# 10. Easy Way to Remember

## `malloc()`

**M = Make memory**

## `calloc()`

**C = Create cleared memory**

## `realloc()`

**R = Resize memory**

## `free()`

**F = Finish and release memory**

---

# 11. Short Exam-Friendly Definitions

## `malloc()`

Allocates a block of memory at runtime but does not initialize it.

## `calloc()`

Allocates memory for multiple elements and initializes them to zero.

## `realloc()`

Changes the size of previously allocated memory.

## `free()`

Releases dynamically allocated memory back to the system.

---

# 12. Practice Questions

## Short Questions

1. What is dynamic memory allocation?
2. What is the difference between `malloc()` and `calloc()`?
3. Why is `free()` important?
4. What does `realloc()` do?
5. What happens if allocated memory is not freed?

---

## Write the Output / Explain

### Q1

```c
int *p = (int *) calloc(3, sizeof(int));
printf("%d %d %d", p[0], p[1], p[2]);
free(p);
```

### Answer

Output:

```c
0 0 0
```

---

### Q2

```c
int *p = (int *) malloc(sizeof(int));
*p = 50;
printf("%d", *p);
free(p);
```

### Answer

Output:

```c
50
```

---

# 13. Final Note

Dynamic memory allocation is very important in C because it allows programs to use memory flexibly during runtime.
To work with it properly, remember these rules:

* allocate memory before using it
* check if allocation was successful
* free memory after use
* never use a pointer after freeing it