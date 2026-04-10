<!-- Of course — below is a **clean, student-friendly English note** that you can **share directly with your student**.

I arranged it in a simple way so that:

* the concept is easy to understand
* the code is short and clear
* the output is given
* the student can revise from it later

--- -->

# ICT 1101 – Structured Programming Language

## Class Note: `union`, `malloc()`, `free()`, `fopen()`, `fclose()`, `fprintf()`, `fscanf()`

---

# 1. `union`

## Definition

A **union** is a user-defined data type in C, similar to a structure.
The main difference is that in a union, **all members share the same memory location**.

That means:

* only one member can hold a meaningful value at a time
* changing one member may affect the others

---

## Example 1

```c id="o63mf1"
#include <stdio.h>

union Data {
    int i;
    float f;
    char ch;
};

int main() {
    union Data d;

    d.i = 10;
    printf("d.i = %d\n", d.i);

    d.f = 5.5;
    printf("d.f = %.1f\n", d.f);

    d.ch = 'A';
    printf("d.ch = %c\n", d.ch);

    return 0;
}
```

## Output

```text id="u8g7ud"
d.i = 10
d.f = 5.5
d.ch = A
```

---

## Example 2: Better for Understanding

```c id="qjvhu2"
#include <stdio.h>

union Data {
    int i;
    float f;
};

int main() {
    union Data d;

    d.i = 25;
    printf("After storing int:\n");
    printf("d.i = %d\n", d.i);

    d.f = 7.5;
    printf("\nAfter storing float:\n");
    printf("d.f = %.1f\n", d.f);
    printf("d.i = %d\n", d.i);

    return 0;
}
```

## Possible Output

```text id="dvy03q"
After storing int:
d.i = 25

After storing float:
d.f = 7.5
d.i = 1089470464
```

## Explanation

After storing `7.5` in `d.f`, the old value of `d.i` is overwritten because both members use the same memory.

## Key Point

**In a union, all members share the same memory.**

---

# 2. `malloc()`

## Definition

`malloc()` stands for **memory allocation**.
It is used to allocate memory during program execution.

This is called **dynamic memory allocation**.

### Header file

```c id="pgl3af"
#include <stdlib.h>
```

---

## Example 1

```c id="c7fe3o"
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *p;

    p = (int *)malloc(sizeof(int));

    *p = 50;

    printf("Value = %d\n", *p);

    return 0;
}
```

## Output

```text id="uuwv2g"
Value = 50
```

## Explanation

* `malloc(sizeof(int))` allocates memory for one integer
* `p` stores the address of that memory
* `*p = 50` stores 50 in that memory location

---

## Example 2: Dynamic Array

```c id="82ebwe"
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *arr;
    int i;

    arr = (int *)malloc(5 * sizeof(int));

    for(i = 0; i < 5; i++) {
        arr[i] = (i + 1) * 10;
    }

    for(i = 0; i < 5; i++) {
        printf("%d ", arr[i]);
    }

    return 0;
}
```

## Output

```text id="pq4kkr"
10 20 30 40 50
```

## Key Point

**`malloc()` allocates memory at runtime.**

---

# 3. `free()`

## Definition

`free()` is used to release memory that was allocated using `malloc()`.

If allocated memory is not released, it may cause **memory leak**.

---

## Example

```c id="cyfvhx"
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *p;

    p = (int *)malloc(sizeof(int));
    *p = 100;

    printf("Before free: %d\n", *p);

    free(p);

    return 0;
}
```

## Output

```text id="xag2cg"
Before free: 100
```

---

## Example with Message

```c id="tdre1s"
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *p;

    p = (int *)malloc(sizeof(int));
    *p = 75;

    printf("Stored value = %d\n", *p);

    free(p);
    printf("Memory released successfully\n");

    return 0;
}
```

## Output

```text id="7nlcbc"
Stored value = 75
Memory released successfully
```

## Key Point

* `malloc()` takes memory
* `free()` releases memory

---

# 4. `fopen()`

## Definition

`fopen()` is used to open a file.

### Syntax

```c id="gtl77u"
FILE *fp;
fp = fopen("filename", "mode");
```

### Common modes

* `"r"` = read
* `"w"` = write
* `"a"` = append

---

## Example

```c id="kdr1d7"
#include <stdio.h>

int main() {
    FILE *fp;

    fp = fopen("data.txt", "w");

    if(fp == NULL) {
        printf("File could not be opened\n");
    } else {
        printf("File opened successfully\n");
    }

    return 0;
}
```

## Output

```text id="1c4ztw"
File opened successfully
```

## Explanation

* `fopen("data.txt", "w")` opens the file in write mode
* if the file does not exist, it is created

## Key Point

**`fopen()` creates a connection between the program and the file.**

---

# 5. `fclose()`

## Definition

`fclose()` is used to close a file after work is finished.

It is important because:

* it saves data properly
* it releases file resources
* it is a good programming practice

---

## Example

```c id="0he5ai"
#include <stdio.h>

int main() {
    FILE *fp;

    fp = fopen("data.txt", "w");

    if(fp == NULL) {
        printf("File could not be opened\n");
    } else {
        printf("File opened successfully\n");
        fclose(fp);
        printf("File closed successfully\n");
    }

    return 0;
}
```

## Output

```text id="a562z3"
File opened successfully
File closed successfully
```

## Key Point

**Always close a file after using it.**

---

# 6. `fprintf()`

## Definition

`fprintf()` is used to write formatted data into a file.

It works like `printf()`, but the output goes to a file instead of the screen.

---

## Example

```c id="2n95g3"
#include <stdio.h>

int main() {
    FILE *fp;

    fp = fopen("data.txt", "w");

    if(fp == NULL) {
        printf("File could not be opened\n");
    } else {
        fprintf(fp, "Name: Rahim\n");
        fprintf(fp, "Age: 20\n");
        printf("Data written to file successfully\n");
        fclose(fp);
    }

    return 0;
}
```

## Console Output

```text id="tdhyce"
Data written to file successfully
```

## File Content (`data.txt`)

```text id="imcqur"
Name: Rahim
Age: 20
```

## Key Point

* `printf()` → writes to screen
* `fprintf()` → writes to file

---

# 7. `fscanf()`

## Definition

`fscanf()` is used to read formatted data from a file.

It works like `scanf()`, but the input comes from a file instead of the keyboard.

---

## File Content First

Suppose `data.txt` contains:

```text id="eljh8u"
Rahim 20
```

## Program

```c id="pn4qwz"
#include <stdio.h>

int main() {
    FILE *fp;
    char name[20];
    int age;

    fp = fopen("data.txt", "r");

    if(fp == NULL) {
        printf("File could not be opened\n");
    } else {
        fscanf(fp, "%s %d", name, &age);
        printf("Name = %s\n", name);
        printf("Age = %d\n", age);
        fclose(fp);
    }

    return 0;
}
```

## Output

```text id="8upca5"
Name = Rahim
Age = 20
```

## Key Point

* `scanf()` → reads from keyboard
* `fscanf()` → reads from file

---

# 8. Combined Example Program

This program shows several concepts together.

```c id="s0fw15"
#include <stdio.h>
#include <stdlib.h>

union Data {
    int i;
    float f;
};

int main() {
    union Data d;
    int *p;
    FILE *fp;
    int num;

    d.i = 25;
    printf("Union int value: %d\n", d.i);

    d.f = 6.5;
    printf("Union float value: %.1f\n", d.f);

    p = (int *)malloc(sizeof(int));
    *p = 100;
    printf("Value from malloc memory: %d\n", *p);
    free(p);
    printf("Memory freed successfully\n");

    fp = fopen("test.txt", "w");
    fprintf(fp, "%d", 500);
    fclose(fp);

    fp = fopen("test.txt", "r");
    fscanf(fp, "%d", &num);
    fclose(fp);

    printf("Value read from file: %d\n", num);

    return 0;
}
```

## Output

```text id="mbvlso"
Union int value: 25
Union float value: 6.5
Value from malloc memory: 100
Memory freed successfully
Value read from file: 500
```

---

# 9. Summary Table

| Topic       | Use                                         |
| ----------- | ------------------------------------------- |
| `union`     | stores different members in the same memory |
| `malloc()`  | allocates memory dynamically                |
| `free()`    | releases allocated memory                   |
| `fopen()`   | opens a file                                |
| `fclose()`  | closes a file                               |
| `fprintf()` | writes formatted data to a file             |
| `fscanf()`  | reads formatted data from a file            |

---

# 10. Important Differences

## `struct` vs `union`

| `struct`                             | `union`                                    |
| ------------------------------------ | ------------------------------------------ |
| each member has separate memory      | all members share the same memory          |
| all members can hold values together | usually one member is meaningful at a time |

## `printf()` vs `fprintf()`

| `printf()`       | `fprintf()`    |
| ---------------- | -------------- |
| writes to screen | writes to file |

## `scanf()` vs `fscanf()`

| `scanf()`           | `fscanf()`      |
| ------------------- | --------------- |
| reads from keyboard | reads from file |

---

# 11. Short Practice Tasks

### Task 1

Write a union with:

* `int id`
* `float marks`

Store one value and print it.

### Task 2

Use `malloc()` to allocate memory for one integer, store `25`, and print it.

### Task 3

Use `malloc()` and then `free()`.

### Task 4

Open a file named `marks.txt` in write mode and close it.

### Task 5

Write your name and roll number into a file using `fprintf()`.

### Task 6

Read a name and age from a file using `fscanf()`.

---

# 12. Quick Review Questions

1. What is a union?
2. What is the main difference between structure and union?
3. What does `malloc()` do?
4. Why do we use `free()`?
5. What is the purpose of `fopen()`?
6. Why should we use `fclose()`?
7. What is the difference between `fprintf()` and `printf()`?
8. What is the difference between `fscanf()` and `scanf()`?

---

# 13. One-Line Revision Notes

* **union** → same memory shared by all members
* **malloc()** → allocates memory during runtime
* **free()** → releases that memory
* **fopen()** → opens file
* **fclose()** → closes file
* **fprintf()** → writes to file
* **fscanf()** → reads from file

<!-- ---

This version is ready to share with your student.
I can also turn it into a **short exam note version** or **10 easy MCQs**. -->
