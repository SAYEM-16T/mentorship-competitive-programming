# Lecture Note: GCD, Euclidean Algorithm, and GCD Properties


## Topic
**Greatest Common Divisor (GCD)**

---

# 1. Learning Objectives

By the end of this lecture, students should be able to:

1. Define GCD.
2. Find GCD using a simple `for` loop.
3. Find GCD using the Euclidean Algorithm.
4. Understand why the Euclidean Algorithm works.
5. Prove that  
   \[
   \gcd(a,b)=\gcd(b,r)
   \]
   where  
   \[
   a=bq+r
   \]
6. Explain important properties of GCD.
7. Write C++ programs for GCD.

---

# 2. What is GCD?

The **Greatest Common Divisor**, or **GCD**, of two integers `a` and `b` is the greatest positive integer that divides both `a` and `b`.

We write:

\[
\gcd(a,b)
\]

Example:

\[
\gcd(20,6)=2
\]

Why?

Divisors of `20`:

```text
1, 2, 4, 5, 10, 20
```

Divisors of `6`:

```text
1, 2, 3, 6
```

Common divisors:

```text
1, 2
```

The greatest common divisor is:

```text
2
```

So,

\[
\gcd(20,6)=2
\]

---

# 3. Meaning of Divides

We write:

\[
d \mid a
\]

This means:

```text
d divides a
```

or

```text
a is perfectly divisible by d
```

That means the remainder is `0`.

Example:

\[
3 \mid 12
\]

because:

```text
12 ÷ 3 = 4 remainder 0
```

So,

\[
12 = 3 \times 4
\]

But:

\[
3 \nmid 14
\]

because:

```text
14 ÷ 3 = 4 remainder 2
```

So `3` does not divide `14`.

---

# 4. First Method: Finding GCD Using a For Loop

This is the simplest programming method.

## Main Idea

To find:

\[
\gcd(a,b)
\]

we check every number from `1` to `min(a,b)`.

The greatest number that divides both `a` and `b` is the GCD.

---

## Example

Find:

\[
\gcd(20,6)
\]

Here:

```text
min(20,6) = 6
```

Now check numbers from `1` to `6`.

| i | 20 % i | 6 % i | Common Divisor? |
|---|--------|-------|-----------------|
| 1 | 0 | 0 | Yes |
| 2 | 0 | 0 | Yes |
| 3 | 2 | 0 | No |
| 4 | 0 | 2 | No |
| 5 | 0 | 1 | No |
| 6 | 2 | 0 | No |

The common divisors are:

```text
1, 2
```

The greatest one is:

```text
2
```

So,

\[
\gcd(20,6)=2
\]

---

# 5. C++ Code: GCD Using For Loop

```cpp
#include <iostream>
using namespace std;

int main() {
    int a, b;
    cin >> a >> b;

    int gcd = 1;

    for (int i = 1; i <= min(a, b); i++) {
        if (a % i == 0 && b % i == 0) {
            gcd = i;
        }
    }

    cout << "GCD = " << gcd << endl;

    return 0;
}
```

---

## Explanation of the Code

```cpp
int gcd = 1;
```

Initially we assume the GCD is `1`.

```cpp
for (int i = 1; i <= min(a, b); i++)
```

We check all numbers from `1` to the smaller number.

```cpp
if (a % i == 0 && b % i == 0)
```

This checks whether `i` divides both `a` and `b`.

```cpp
gcd = i;
```

If `i` divides both numbers, we update `gcd`.

Since the loop goes from small to large, the final value of `gcd` will be the greatest common divisor.

---

# 6. Problem with the For Loop Method

The for-loop method is easy to understand, but it is slow for large numbers.

Example:

```text
a = 1000000000
b = 999999937
```

The loop may run up to almost one billion times.

So we need a faster method.

That faster method is called the **Euclidean Algorithm**.

---

# 7. Euclidean Algorithm

The Euclidean Algorithm is based on this important property:

If

\[
a=bq+r
\]

then

\[
\gcd(a,b)=\gcd(b,r)
\]

Here:

- `a` is the larger number
- `b` is the smaller number
- `q` is the quotient
- `r` is the remainder

---

# 8. Visual Idea of Euclidean Algorithm

Suppose:

\[
20 = 6 \times 3 + 2
\]

This means:

```text
20 = 6 + 6 + 6 + 2
```

So `20` contains three full groups of `6`, and the leftover part is `2`.

Now:

\[
\gcd(20,6)=\gcd(6,2)
\]

Why?

Because the part `6 + 6 + 6` is already made from `6`.

The only new part in `20` is the leftover:

```text
2
```

So instead of finding the GCD of:

```text
20 and 6
```

we can find the GCD of:

```text
6 and 2
```

This makes the problem smaller.

---

# 9. Student-Friendly Explanation: Why Does the Remainder Work?

We know:

```text
20 = 6 + 6 + 6 + 2
```

Now suppose some number `d` divides both `20` and `6`.

That means:

```text
20 = d × something
6  = d × something
```

If `d` divides `6`, then `d` also divides:

```text
6 + 6 + 6
```

because adding multiples of `d` still gives a multiple of `d`.

Now:

```text
20 = 6 + 6 + 6 + 2
```

So:

```text
2 = 20 - 6 - 6 - 6
```

Since `d` divides `20`, and `d` divides every `6`, then `d` must also divide:

```text
20 - 6 - 6 - 6
```

So `d` also divides:

```text
2
```

Therefore, any common divisor of `20` and `6` is also a common divisor of `6` and `2`.

So:

\[
\gcd(20,6)=\gcd(6,2)
\]

---

# 10. Concrete Example

Common divisor of `20` and `6`:

```text
2
```

Check:

```text
20 ÷ 2 = 10
6 ÷ 2 = 3
```

Now leftover:

```text
20 - 6 - 6 - 6 = 2
```

Check:

```text
2 ÷ 2 = 1
```

So the same divisor also divides the leftover.

This is the heart of the Euclidean Algorithm.

---

# 11. Euclidean Algorithm Step-by-Step Example

Find:

\[
\gcd(20,6)
\]

Step 1:

\[
20 = 6 \times 3 + 2
\]

So:

\[
\gcd(20,6)=\gcd(6,2)
\]

Step 2:

\[
6 = 2 \times 3 + 0
\]

When the remainder becomes `0`, we stop.

The last non-zero remainder is:

```text
2
```

So:

\[
\gcd(20,6)=2
\]

---

# 12. Another Example

Find:

\[
\gcd(240,46)
\]

Step 1:

\[
240 = 46 \times 5 + 10
\]

So:

\[
\gcd(240,46)=\gcd(46,10)
\]

Step 2:

\[
46 = 10 \times 4 + 6
\]

So:

\[
\gcd(46,10)=\gcd(10,6)
\]

Step 3:

\[
10 = 6 \times 1 + 4
\]

So:

\[
\gcd(10,6)=\gcd(6,4)
\]

Step 4:

\[
6 = 4 \times 1 + 2
\]

So:

\[
\gcd(6,4)=\gcd(4,2)
\]

Step 5:

\[
4 = 2 \times 2 + 0
\]

Now the remainder is `0`.

So the GCD is the last non-zero remainder:

\[
\gcd(240,46)=2
\]

---

# 13. C++ Code: Euclidean Algorithm Using While Loop

```cpp
#include <iostream>
using namespace std;

int gcd(int a, int b) {
    while (b != 0) {
        int r = a % b;
        a = b;
        b = r;
    }

    return a;
}

int main() {
    int a, b;
    cin >> a >> b;

    cout << "GCD = " << gcd(a, b) << endl;

    return 0;
}
```

---

## Dry Run

Input:

```text
240 46
```

| a | b | r = a % b |
|---|---|-----------|
| 240 | 46 | 10 |
| 46 | 10 | 6 |
| 10 | 6 | 4 |
| 6 | 4 | 2 |
| 4 | 2 | 0 |

When `b = 0`, stop.

The answer is:

```text
a = 2
```

So:

\[
\gcd(240,46)=2
\]

---

# 14. Recursive C++ Code for Euclidean Algorithm

```cpp
#include <iostream>
using namespace std;

int gcd(int a, int b) {
    if (b == 0) {
        return a;
    }

    return gcd(b, a % b);
}

int main() {
    int a, b;
    cin >> a >> b;

    cout << "GCD = " << gcd(a, b) << endl;

    return 0;
}
```

---

# 15. Proof of the Main GCD Property

We want to prove:

If

\[
a=bq+r
\]

then

\[
\gcd(a,b)=\gcd(b,r)
\]

---

## Step 1: From `a, b` to `b, r`

Suppose `d` divides both `a` and `b`.

So:

\[
d \mid a
\]

and

\[
d \mid b
\]

Since:

\[
r=a-bq
\]

and `d` divides both `a` and `bq`, then `d` also divides:

\[
a-bq
\]

So:

\[
d \mid r
\]

Therefore, every common divisor of `a` and `b` is also a common divisor of `b` and `r`.

---

## Step 2: From `b, r` to `a, b`

Suppose `d` divides both `b` and `r`.

So:

\[
d \mid b
\]

and

\[
d \mid r
\]

Since:

\[
a=bq+r
\]

and `d` divides both `bq` and `r`, then `d` also divides:

\[
bq+r
\]

So:

\[
d \mid a
\]

Therefore, every common divisor of `b` and `r` is also a common divisor of `a` and `b`.

---

## Final Conclusion

The common divisors of `(a,b)` and `(b,r)` are the same.

Therefore their greatest common divisor is also the same.

So:

\[
\boxed{\gcd(a,b)=\gcd(b,r)}
\]

---

# 16. Important GCD Properties

## Property 1: Order Does Not Matter

\[
\gcd(a,b)=\gcd(b,a)
\]

Example:

\[
\gcd(12,8)=\gcd(8,12)=4
\]

---

## Property 2: GCD with Zero

\[
\gcd(a,0)=|a|
\]

Example:

\[
\gcd(15,0)=15
\]

Why?

Because every non-zero integer divides `0`, and the greatest divisor of `a` is `|a|`.

---

## Property 3: Negative Sign Does Not Matter

\[
\gcd(a,b)=\gcd(|a|,|b|)
\]

Example:

\[
\gcd(-12,8)=\gcd(12,8)=4
\]

---

## Property 4: GCD of a Number with Itself

\[
\gcd(a,a)=|a|
\]

Example:

\[
\gcd(9,9)=9
\]

---

## Property 5: If One Number Divides Another

If:

\[
a \mid b
\]

then:

\[
\gcd(a,b)=|a|
\]

Example:

\[
4 \mid 20
\]

So:

\[
\gcd(4,20)=4
\]

---

## Property 6: Coprime Numbers

If:

\[
\gcd(a,b)=1
\]

then `a` and `b` are called **coprime** or **relatively prime**.

Example:

\[
\gcd(8,15)=1
\]

So `8` and `15` are coprime.

Important note:

Coprime numbers do not have to be prime numbers.

`8` and `15` are both composite, but they are coprime.

---

## Property 7: Consecutive Integers Are Coprime

For any integer `n`:

\[
\gcd(n,n+1)=1
\]

Example:

\[
\gcd(10,11)=1
\]

Why?

If a number divides both `n` and `n+1`, then it must divide their difference:

\[
(n+1)-n=1
\]

Only `1` divides `1`.

So the GCD is `1`.

---

## Property 8: GCD and LCM Relation

For positive integers `a` and `b`:

\[
\gcd(a,b)\times \operatorname{lcm}(a,b)=a\times b
\]

So:

\[
\operatorname{lcm}(a,b)=\frac{a\times b}{\gcd(a,b)}
\]

Example:

\[
a=12,\quad b=18
\]

\[
\gcd(12,18)=6
\]

So:

\[
\operatorname{lcm}(12,18)=\frac{12\times18}{6}=36
\]

---

# 17. Comparison: For Loop vs Euclidean Algorithm

| Method | Idea | Speed | Good For |
|---|---|---|---|
| For Loop | Check all numbers from `1` to `min(a,b)` | Slow | Beginners |
| Euclidean Algorithm | Repeatedly use remainder | Fast | Real programming and mathematics |

---

# 18. Time Complexity

## For Loop Method

The loop runs up to:

\[
\min(a,b)
\]

So the time complexity is:

\[
O(\min(a,b))
\]

---

## Euclidean Algorithm

The Euclidean Algorithm is much faster.

Its time complexity is approximately:

\[
O(\log(\min(a,b)))
\]

This is why the Euclidean Algorithm is used in real programming.

---

# 19. Class Demonstration Plan

## Step 1: Ask Students

Ask:

```text
What is gcd(20, 6)?
```

Let students list divisors.

Then show:

```text
Divisors of 20: 1, 2, 4, 5, 10, 20
Divisors of 6 : 1, 2, 3, 6
Common divisors: 1, 2
GCD = 2
```

---

## Step 2: Show For Loop Method

Explain that the computer can check all possible divisors one by one.

Show this table:

| i | 20 % i | 6 % i | Common divisor? |
|---|--------|-------|-----------------|
| 1 | 0 | 0 | Yes |
| 2 | 0 | 0 | Yes |
| 3 | 2 | 0 | No |
| 4 | 0 | 2 | No |
| 5 | 0 | 1 | No |
| 6 | 2 | 0 | No |

Then show the C++ code.

---

## Step 3: Show Why For Loop Is Slow

Give this example:

```text
gcd(1000000000, 999999937)
```

Explain that checking many numbers is inefficient.

---

## Step 4: Introduce Euclidean Algorithm

Write:

```text
20 = 6 × 3 + 2
```

Then visualize:

```text
20 = 6 + 6 + 6 + 2
```

Explain:

```text
The useful new part is the leftover 2.
So gcd(20, 6) becomes gcd(6, 2).
```

---

## Step 5: Visual Proof

Show:

```text
If d divides 20 and d divides 6,
then d divides 6 + 6 + 6.
```

Since:

```text
20 = 6 + 6 + 6 + 2
```

then:

```text
2 = 20 - 6 - 6 - 6
```

So `d` also divides `2`.

Therefore:

```text
Any common divisor of 20 and 6 also divides 6 and 2.
```

So:

```text
gcd(20, 6) = gcd(6, 2)
```

---

# 20. Practice Problems

## Problem 1

Find using the for-loop idea:

\[
\gcd(18,24)
\]

---

## Problem 2

Find using the Euclidean Algorithm:

\[
\gcd(252,198)
\]

---

## Problem 3

Find using the Euclidean Algorithm:

\[
\gcd(240,46)
\]

---

## Problem 4

Prove:

\[
\gcd(n,n+1)=1
\]

---

## Problem 5

Write a C++ program to find GCD using a for loop.

---

## Problem 6

Write a C++ program to find GCD using the Euclidean Algorithm.

---

# 21. Solutions to Selected Practice Problems

## Solution 1

Find:

\[
\gcd(18,24)
\]

Divisors of `18`:

```text
1, 2, 3, 6, 9, 18
```

Divisors of `24`:

```text
1, 2, 3, 4, 6, 8, 12, 24
```

Common divisors:

```text
1, 2, 3, 6
```

So:

\[
\gcd(18,24)=6
\]

---

## Solution 2

Find:

\[
\gcd(252,198)
\]

\[
252 = 198 \times 1 + 54
\]

\[
198 = 54 \times 3 + 36
\]

\[
54 = 36 \times 1 + 18
\]

\[
36 = 18 \times 2 + 0
\]

So:

\[
\gcd(252,198)=18
\]

---

## Solution 3

Find:

\[
\gcd(240,46)
\]

\[
240 = 46 \times 5 + 10
\]

\[
46 = 10 \times 4 + 6
\]

\[
10 = 6 \times 1 + 4
\]

\[
6 = 4 \times 1 + 2
\]

\[
4 = 2 \times 2 + 0
\]

So:

\[
\gcd(240,46)=2
\]

---

# 22. Final Summary

GCD means the greatest number that divides two numbers exactly.

The for-loop method is simple but slow.

The Euclidean Algorithm is fast because it uses this property:

\[
\gcd(a,b)=\gcd(b,r)
\]

where:

\[
a=bq+r
\]

The main reason this works is:

```text
If a number divides both a and b,
then it also divides a - bq.
```

So the remainder keeps the common divisor information, but makes the problem smaller.

That is why the Euclidean Algorithm is one of the most important algorithms in mathematics and computer science.


---

# 23. C++ Code Section: Normal GCD and Euclidean Algorithm GCD

This section is useful for programming class demonstration.

---

## 23.1 Normal GCD Using For Loop

### Idea

To find:

\[
\gcd(a,b)
\]

we check every number from `1` to `min(a,b)`.

If a number divides both `a` and `b`, then it is a common divisor.

The greatest such number is the GCD.

---

### C++ Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int a, b;
    cin >> a >> b;

    int gcd = 1;

    for (int i = 1; i <= min(a, b); i++) {
        if (a % i == 0 && b % i == 0) {
            gcd = i;
        }
    }

    cout << "GCD = " << gcd << endl;

    return 0;
}
```

---

### Example Input

```text
20 6
```

### Output

```text
GCD = 2
```

---

### Explanation

For `20` and `6`, the loop checks:

```text
i = 1, 2, 3, 4, 5, 6
```

Common divisors are:

```text
1, 2
```

The greatest common divisor is:

```text
2
```

So:

\[
\gcd(20,6)=2
\]

---

## 23.2 Normal GCD Using For Loop with Function

This version is cleaner because the GCD logic is inside a function.

```cpp
#include <iostream>
using namespace std;

int findGCD(int a, int b) {
    int gcd = 1;

    for (int i = 1; i <= min(a, b); i++) {
        if (a % i == 0 && b % i == 0) {
            gcd = i;
        }
    }

    return gcd;
}

int main() {
    int a, b;
    cin >> a >> b;

    cout << "GCD = " << findGCD(a, b) << endl;

    return 0;
}
```

---

# 24. C++ Code: GCD Using Euclidean Algorithm

## Idea

The Euclidean Algorithm uses this property:

\[
\gcd(a,b)=\gcd(b,a \% b)
\]

We repeatedly replace:

```text
a with b
b with a % b
```

until `b` becomes `0`.

When `b = 0`, the answer is `a`.

---

## 24.1 Euclidean Algorithm Using While Loop

```cpp
#include <iostream>
using namespace std;

int gcd(int a, int b) {
    while (b != 0) {
        int r = a % b;
        a = b;
        b = r;
    }

    return a;
}

int main() {
    int a, b;
    cin >> a >> b;

    cout << "GCD = " << gcd(a, b) << endl;

    return 0;
}
```

---

### Example Input

```text
240 46
```

### Output

```text
GCD = 2
```

---

### Dry Run

| Step | a | b | r = a % b |
|---|---:|---:|---:|
| 1 | 240 | 46 | 10 |
| 2 | 46 | 10 | 6 |
| 3 | 10 | 6 | 4 |
| 4 | 6 | 4 | 2 |
| 5 | 4 | 2 | 0 |

When `b = 0`, stop.

The final value of `a` is:

```text
2
```

So:

\[
\gcd(240,46)=2
\]

---

## 24.2 Euclidean Algorithm Using Recursion

```cpp
#include <iostream>
using namespace std;

int gcd(int a, int b) {
    if (b == 0) {
        return a;
    }

    return gcd(b, a % b);
}

int main() {
    int a, b;
    cin >> a >> b;

    cout << "GCD = " << gcd(a, b) << endl;

    return 0;
}
```

---

## 24.3 Comparison of the Two Codes

| Method | Code Style | Speed | Easy to Understand? |
|---|---|---|---|
| For Loop GCD | Checks all possible divisors | Slow | Very easy |
| Euclidean Algorithm | Uses remainder repeatedly | Fast | Slightly advanced |

---

## 24.4 Which One Should Students Learn First?

Students should learn in this order:

```text
1. Divisibility idea
2. For loop GCD
3. Problem with for loop method
4. Euclidean Algorithm
5. Proof of gcd(a,b) = gcd(b,r)
6. Recursive GCD
```

The for-loop method helps students understand what GCD means.

The Euclidean Algorithm helps students understand how to find GCD efficiently.
