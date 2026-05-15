# Lecture Note: Sieve of Eratosthenes with Step-by-Step Visualization


## Topic
**Finding Prime Numbers Using the Sieve of Eratosthenes**

---

# 1. Learning Objectives

By the end of this lecture, students should be able to:

1. Define prime and composite numbers.
2. Explain the idea of the Sieve of Eratosthenes.
3. Visualize how numbers from `1` to `100` are crossed out step by step.
4. Understand why we only need to process numbers up to \(\sqrt{n}\).
5. Understand why marking starts from \(i \times i\).
6. Analyze the time and space complexity of the sieve.
7. Write C++ code for the Sieve of Eratosthenes.
8. Write C++ code that prints a step-by-step visualization.

---

# 2. What is a Prime Number?

A **prime number** is a positive integer greater than `1` that has exactly two positive divisors:

```text
1 and itself
```

Examples:

```text
2, 3, 5, 7, 11, 13, 17
```

---

# 3. What is a Composite Number?

A **composite number** is a positive integer greater than `1` that has more than two divisors.

Examples:

```text
4, 6, 8, 9, 10, 12
```

Example:

```text
6 = 1 × 6
6 = 2 × 3
```

So `6` has more than two divisors. Therefore, `6` is composite.

---

# 4. Important Note About 1

The number `1` is neither prime nor composite.

So in this lecture, we will mark it as:

```text
1(N)
```

Here:

```text
N = Not Prime
```

---

# 5. What is the Sieve of Eratosthenes?

The **Sieve of Eratosthenes** is an efficient algorithm for finding all prime numbers from `1` to `n`.

The main idea is:

```text
Start from the first prime number.
Cross out its multiples.
Move to the next uncrossed number.
Repeat the process.
The numbers that remain uncrossed are prime.
```

---

# 6. Notation Used in This Visualization

In our visualization, we will use the following notation:

```text
1(N)   means 1 is not prime
2(P)   means 2 is prime
4(2)   means 4 is crossed out by 2
9(3)   means 9 is crossed out by 3
25(5)  means 25 is crossed out by 5
49(7)  means 49 is crossed out by 7
```

Important:

If a number can be crossed out by multiple primes, we will write the prime that crossed it out **first**.

Example:

```text
30 is divisible by 2, 3, and 5.
```

But in the sieve, `30` is first crossed out by `2`.

So we write:

```text
30(2)
```

Another example:

```text
45 is divisible by 3 and 5.
```

But `45` is first crossed out by `3`.

So we write:

```text
45(3)
```

---

# 7. Initial State: Numbers from 1 to 100

At the beginning, no number has been crossed out yet.

```text
1(N)    2       3       4       5       6       7       8       9       10
11      12      13      14      15      16      17      18      19      20
21      22      23      24      25      26      27      28      29      30
31      32      33      34      35      36      37      38      39      40
41      42      43      44      45      46      47      48      49      50
51      52      53      54      55      56      57      58      59      60
61      62      63      64      65      66      67      68      69      70
71      72      73      74      75      76      77      78      79      80
81      82      83      84      85      86      87      88      89      90
91      92      93      94      95      96      97      98      99      100
```

---

# 8. Step 1: Cross Out Multiples of 2

The first prime number is:

```text
2
```

So we mark:

```text
2(P)
```

Now we cross out all multiples of `2`, except `2` itself.

Multiples of `2`:

```text
4, 6, 8, 10, 12, 14, 16, 18, 20, ...
```

After crossing them out, the visualization becomes:

```text
1(N)    2(P)    3       4(2)    5       6(2)    7       8(2)    9       10(2)
11      12(2)   13      14(2)   15      16(2)   17      18(2)   19      20(2)
21      22(2)   23      24(2)   25      26(2)   27      28(2)   29      30(2)
31      32(2)   33      34(2)   35      36(2)   37      38(2)   39      40(2)
41      42(2)   43      44(2)   45      46(2)   47      48(2)   49      50(2)
51      52(2)   53      54(2)   55      56(2)   57      58(2)   59      60(2)
61      62(2)   63      64(2)   65      66(2)   67      68(2)   69      70(2)
71      72(2)   73      74(2)   75      76(2)   77      78(2)   79      80(2)
81      82(2)   83      84(2)   85      86(2)   87      88(2)   89      90(2)
91      92(2)   93      94(2)   95      96(2)   97      98(2)   99      100(2)
```

---

# 9. Step 2: Cross Out Multiples of 3

The next uncrossed number is:

```text
3
```

So `3` is prime.

We mark:

```text
3(P)
```

Now we cross out multiples of `3`.

Multiples of `3`:

```text
6, 9, 12, 15, 18, 21, 24, 27, ...
```

But some numbers, such as `6`, `12`, `18`, and `24`, were already crossed out by `2`.

So the new numbers crossed out by `3` are:

```text
9, 15, 21, 27, 33, 39, 45, 51, 57, 63, 69, 75, 81, 87, 93, 99
```

After this step:

```text
1(N)    2(P)    3(P)    4(2)    5       6(2)    7       8(2)    9(3)    10(2)
11      12(2)   13      14(2)   15(3)   16(2)   17      18(2)   19      20(2)
21(3)   22(2)   23      24(2)   25      26(2)   27(3)   28(2)   29      30(2)
31      32(2)   33(3)   34(2)   35      36(2)   37      38(2)   39(3)   40(2)
41      42(2)   43      44(2)   45(3)   46(2)   47      48(2)   49      50(2)
51(3)   52(2)   53      54(2)   55      56(2)   57(3)   58(2)   59      60(2)
61      62(2)   63(3)   64(2)   65      66(2)   67      68(2)   69(3)   70(2)
71      72(2)   73      74(2)   75(3)   76(2)   77      78(2)   79      80(2)
81(3)   82(2)   83      84(2)   85      86(2)   87(3)   88(2)   89      90(2)
91      92(2)   93(3)   94(2)   95      96(2)   97      98(2)   99(3)   100(2)
```

---

# 10. Step 3: Cross Out Multiples of 5

The next uncrossed number is:

```text
5
```

So `5` is prime.

We mark:

```text
5(P)
```

Now we cross out multiples of `5`.

Multiples of `5`:

```text
10, 15, 20, 25, 30, 35, 40, ...
```

But many of them have already been crossed out by `2` or `3`.

The new numbers crossed out by `5` are:

```text
25, 35, 55, 65, 85, 95
```

After this step:

```text
1(N)    2(P)    3(P)    4(2)    5(P)    6(2)    7       8(2)    9(3)    10(2)
11      12(2)   13      14(2)   15(3)   16(2)   17      18(2)   19      20(2)
21(3)   22(2)   23      24(2)   25(5)   26(2)   27(3)   28(2)   29      30(2)
31      32(2)   33(3)   34(2)   35(5)   36(2)   37      38(2)   39(3)   40(2)
41      42(2)   43      44(2)   45(3)   46(2)   47      48(2)   49      50(2)
51(3)   52(2)   53      54(2)   55(5)   56(2)   57(3)   58(2)   59      60(2)
61      62(2)   63(3)   64(2)   65(5)   66(2)   67      68(2)   69(3)   70(2)
71      72(2)   73      74(2)   75(3)   76(2)   77      78(2)   79      80(2)
81(3)   82(2)   83      84(2)   85(5)   86(2)   87(3)   88(2)   89      90(2)
91      92(2)   93(3)   94(2)   95(5)   96(2)   97      98(2)   99(3)   100(2)
```

---

# 11. Step 4: Cross Out Multiples of 7

The next uncrossed number is:

```text
7
```

So `7` is prime.

We mark:

```text
7(P)
```

Now we cross out multiples of `7`.

Multiples of `7`:

```text
14, 21, 28, 35, 42, 49, 56, 63, 70, 77, 84, 91, 98
```

Many of them were already crossed out by `2`, `3`, or `5`.

The new numbers crossed out by `7` are:

```text
49, 77, 91
```

After this step:

```text
1(N)    2(P)    3(P)    4(2)    5(P)    6(2)    7(P)    8(2)    9(3)    10(2)
11      12(2)   13      14(2)   15(3)   16(2)   17      18(2)   19      20(2)
21(3)   22(2)   23      24(2)   25(5)   26(2)   27(3)   28(2)   29      30(2)
31      32(2)   33(3)   34(2)   35(5)   36(2)   37      38(2)   39(3)   40(2)
41      42(2)   43      44(2)   45(3)   46(2)   47      48(2)   49(7)   50(2)
51(3)   52(2)   53      54(2)   55(5)   56(2)   57(3)   58(2)   59      60(2)
61      62(2)   63(3)   64(2)   65(5)   66(2)   67      68(2)   69(3)   70(2)
71      72(2)   73      74(2)   75(3)   76(2)   77(7)   78(2)   79      80(2)
81(3)   82(2)   83      84(2)   85(5)   86(2)   87(3)   88(2)   89      90(2)
91(7)   92(2)   93(3)   94(2)   95(5)   96(2)   97      98(2)   99(3)   100(2)
```

---

# 12. Why Do We Stop at 7 for Numbers up to 100?

We are finding primes up to:

\[
100
\]

We only need to check prime numbers up to:

\[
\sqrt{100}=10
\]

The prime numbers less than or equal to `10` are:

```text
2, 3, 5, 7
```

So after processing `2`, `3`, `5`, and `7`, we are done.

---

# 13. Why Checking up to Square Root is Enough

Suppose a number `x` is composite.

Then:

\[
x = a \times b
\]

If both `a` and `b` were greater than \(\sqrt{x}\), then:

\[
a \times b > x
\]

That is impossible.

Therefore, at least one factor of a composite number must be less than or equal to:

\[
\sqrt{x}
\]

So if a number has not been crossed out by any prime up to \(\sqrt{n}\), then it is prime.

---

# 14. Final Prime Marking

After processing `2`, `3`, `5`, and `7`, all unmarked numbers are prime.

Final visualization:

```text
1(N)    2(P)    3(P)    4(2)    5(P)    6(2)    7(P)    8(2)    9(3)    10(2)
11(P)   12(2)   13(P)   14(2)   15(3)   16(2)   17(P)   18(2)   19(P)   20(2)
21(3)   22(2)   23(P)   24(2)   25(5)   26(2)   27(3)   28(2)   29(P)   30(2)
31(P)   32(2)   33(3)   34(2)   35(5)   36(2)   37(P)   38(2)   39(3)   40(2)
41(P)   42(2)   43(P)   44(2)   45(3)   46(2)   47(P)   48(2)   49(7)   50(2)
51(3)   52(2)   53(P)   54(2)   55(5)   56(2)   57(3)   58(2)   59(P)   60(2)
61(P)   62(2)   63(3)   64(2)   65(5)   66(2)   67(P)   68(2)   69(3)   70(2)
71(P)   72(2)   73(P)   74(2)   75(3)   76(2)   77(7)   78(2)   79(P)   80(2)
81(3)   82(2)   83(P)   84(2)   85(5)   86(2)   87(3)   88(2)   89(P)   90(2)
91(7)   92(2)   93(3)   94(2)   95(5)   96(2)   97(P)   98(2)   99(3)   100(2)
```

---

# 15. Prime Numbers from 1 to 100

The prime numbers from `1` to `100` are:

```text
2, 3, 5, 7,
11, 13, 17, 19,
23, 29,
31, 37,
41, 43, 47,
53, 59,
61, 67,
71, 73, 79,
83, 89,
97
```

Total number of primes from `1` to `100`:

```text
25
```

---

# 16. Why Do We Start Marking from i × i?

When we process a prime number `i`, we start crossing out from:

\[
i \times i
\]

not from:

\[
2 \times i
\]

Why?

Because smaller multiples have already been crossed out by smaller primes.

Example:

When `i = 5`, the multiples of `5` are:

```text
5 × 2 = 10
5 × 3 = 15
5 × 4 = 20
5 × 5 = 25
```

But:

```text
10 was already crossed out by 2
15 was already crossed out by 3
20 was already crossed out by 2
```

So the first new number to cross out using `5` is:

```text
25
```

That is:

\[
5 \times 5
\]

So we start from:

```cpp
j = i * i;
```

---

# 17. Time Complexity

The time complexity of the Sieve of Eratosthenes is:

\[
O(n \log \log n)
\]

---

## 17.1 Why Not O(n²)?

We are not checking every pair of numbers.

We only mark multiples of prime numbers.

For example:

- For `2`, we mark about \(n/2\) numbers.
- For `3`, we mark about \(n/3\) numbers.
- For `5`, we mark about \(n/5\) numbers.
- For `7`, we mark about \(n/7\) numbers.

So the total work is roughly:

\[
\frac{n}{2}+\frac{n}{3}+\frac{n}{5}+\frac{n}{7}+\frac{n}{11}+\cdots
\]

This is:

\[
n\left(\frac{1}{2}+\frac{1}{3}+\frac{1}{5}+\frac{1}{7}+\frac{1}{11}+\cdots\right)
\]

The sum of reciprocals of primes grows like:

\[
\log \log n
\]

Therefore:

\[
\text{Time Complexity}=O(n \log \log n)
\]

---

## 17.2 Simple Way to Explain Complexity 
The sieve is fast because it does not test each number separately for primality.

Instead, it removes many composite numbers at once.

Example:

When we process `2`, we remove:

```text
4, 6, 8, 10, 12, ...
```

When we process `3`, we remove:

```text
9, 15, 21, 27, ...
```

When we process `5`, we remove:

```text
25, 35, 55, 65, ...
```

So the algorithm eliminates numbers in groups.

That is why it is much faster than checking every number one by one.

---

# 18. Space Complexity

The sieve uses an array of size:

```text
n + 1
```

Usually we use:

```cpp
vector<bool> isPrime(n + 1, true);
```

So the space complexity is:

\[
O(n)
\]

---

# 19. Complexity Comparison

| Method | Purpose | Time Complexity | Space Complexity |
|---|---|---:|---:|
| Trial division for each number | Check every number separately | \(O(n\sqrt{n})\) | \(O(1)\) |
| Sieve of Eratosthenes | Generate all primes up to n | \(O(n\log\log n)\) | \(O(n)\) |

---

# 20. Standard C++ Code: Sieve of Eratosthenes

This code prints all prime numbers from `1` to `n`.

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    int n;
    cin >> n;

    vector<bool> isPrime(n + 1, true);

    if (n >= 0) isPrime[0] = false;
    if (n >= 1) isPrime[1] = false;

    for (int i = 2; i * i <= n; i++) {
        if (isPrime[i]) {
            for (int j = i * i; j <= n; j += i) {
                isPrime[j] = false;
            }
        }
    }

    cout << "Prime numbers from 1 to " << n << " are:" << endl;

    for (int i = 2; i <= n; i++) {
        if (isPrime[i]) {
            cout << i << " ";
        }
    }

    cout << endl;

    return 0;
}
```

---

## Sample Input

```text
100
```

## Sample Output

```text
Prime numbers from 1 to 100 are:
2 3 5 7 11 13 17 19 23 29 31 37 41 43 47 53 59 61 67 71 73 79 83 89 97
```

---

# 21. C++ Code with Function

This version is useful for competitive programming or reusable code.

```cpp
#include <iostream>
#include <vector>
using namespace std;

vector<int> sieve(int n) {
    vector<bool> isPrime(n + 1, true);
    vector<int> primes;

    if (n >= 0) isPrime[0] = false;
    if (n >= 1) isPrime[1] = false;

    for (int i = 2; i * i <= n; i++) {
        if (isPrime[i]) {
            for (int j = i * i; j <= n; j += i) {
                isPrime[j] = false;
            }
        }
    }

    for (int i = 2; i <= n; i++) {
        if (isPrime[i]) {
            primes.push_back(i);
        }
    }

    return primes;
}

int main() {
    int n;
    cin >> n;

    vector<int> primes = sieve(n);

    for (int p : primes) {
        cout << p << " ";
    }

    cout << endl;

    return 0;
}
```

---

# 22. C++ Code: Step-by-Step Visualization from 1 to 100

This code shows the same style of visualization used in this lecture.

It prints the grid:

1. Initial state
2. After crossing by `2`
3. After crossing by `3`
4. After crossing by `5`
5. After crossing by `7`
6. Final prime marking

```cpp
#include <iostream>
#include <vector>
#include <iomanip>
#include <string>
using namespace std;

void printGrid(const vector<int>& cutBy, const vector<bool>& selectedPrime, bool finalMarking) {
    int n = 100;

    for (int i = 1; i <= n; i++) {
        string cell;

        if (i == 1) {
            cell = "1(N)";
        }
        else if (cutBy[i] != 0) {
            cell = to_string(i) + "(" + to_string(cutBy[i]) + ")";
        }
        else if (selectedPrime[i] || finalMarking) {
            cell = to_string(i) + "(P)";
        }
        else {
            cell = to_string(i);
        }

        cout << left << setw(9) << cell;

        if (i % 10 == 0) {
            cout << endl;
        }
    }

    cout << endl;
}

int main() {
    const int n = 100;

    vector<int> cutBy(n + 1, 0);
    vector<bool> selectedPrime(n + 1, false);

    cout << "Initial State:" << endl;
    printGrid(cutBy, selectedPrime, false);

    vector<int> processPrimes = {2, 3, 5, 7};

    for (int p : processPrimes) {
        selectedPrime[p] = true;

        for (int j = p * p; j <= n; j += p) {
            if (cutBy[j] == 0) {
                cutBy[j] = p;
            }
        }

        cout << "After crossing multiples of " << p << ":" << endl;
        printGrid(cutBy, selectedPrime, false);
    }

    cout << "Final Prime Marking:" << endl;
    printGrid(cutBy, selectedPrime, true);

    return 0;
}
```

---

# 23. Explanation of the Visualization Code

## cutBy Array

```cpp
vector<int> cutBy(n + 1, 0);
```

This stores which prime first crossed out a number.

Example:

```text
cutBy[4] = 2
cutBy[9] = 3
cutBy[25] = 5
cutBy[49] = 7
```

So the output becomes:

```text
4(2), 9(3), 25(5), 49(7)
```

---

## selectedPrime Array

```cpp
vector<bool> selectedPrime(n + 1, false);
```

This stores which prime has already been selected in the sieve process.

Example:

After processing `2`:

```text
2(P)
```

After processing `3`:

```text
2(P), 3(P)
```

After processing `5`:

```text
2(P), 3(P), 5(P)
```

---

## Why Use p × p in the Code?

```cpp
for (int j = p * p; j <= n; j += p)
```

Because smaller multiples of `p` have already been crossed out by smaller primes.

Example:

For `p = 5`:

```text
10, 15, 20
```

are already crossed out.

So we start from:

```text
25
```

---

# 24. Short Classroom Script

You can explain the algorithm to students like this:

```text
First, we do not know which numbers are prime.

We start from 2.
Since 2 is the first uncrossed number, 2 is prime.
Now we cross out all multiples of 2.

Next, the first uncrossed number is 3.
So 3 is prime.
Now we cross out all multiples of 3.

Next, the first uncrossed number is 5.
So 5 is prime.
Now we cross out all multiples of 5.

Next, the first uncrossed number is 7.
So 7 is prime.
Now we cross out all multiples of 7.

For numbers up to 100, we stop here because sqrt(100) = 10.
The primes less than or equal to 10 are 2, 3, 5, and 7.

Finally, every number that has not been crossed out is prime.
```

---

# 25. Common Student Questions

## Question 1: Why is 1 not prime?

Because a prime number must have exactly two positive divisors.

The number `1` has only one positive divisor:

```text
1
```

So `1` is not prime.

---

## Question 2: Why do we cross out multiples?

Because if a number is a multiple of another number greater than `1`, then it has more than two divisors.

Example:

```text
12 = 2 × 6
```

So `12` is not prime.

---

## Question 3: Why do we not cross out the prime itself?

When we process `2`, we do not cross out `2`.

Because `2` is prime.

We only cross out:

```text
2 × 2, 2 × 3, 2 × 4, ...
```

---

## Question 4: Why is 49 crossed out by 7?

Because:

```text
49 = 7 × 7
```

It was not crossed out by `2`, `3`, or `5`.

So when we process `7`, `49` is crossed out.

Therefore, we write:

```text
49(7)
```

---

# 26. Practice Problems

## Problem 1

Using the sieve method, find all primes from `1` to `50`.

---

## Problem 2

In the sieve from `1` to `100`, which prime first crosses out `77`?

Answer:

```text
7
```

Because:

```text
77 = 7 × 11
```

So:

```text
77(7)
```

---

## Problem 3

Why is `30` written as `30(2)` and not `30(3)` or `30(5)`?

Answer:

`30` is divisible by `2`, `3`, and `5`.

But in the sieve, it is first crossed out by `2`.

So:

```text
30(2)
```

---

## Problem 4

Why do we only process up to `sqrt(n)`?

---

## Problem 5

Write C++ code to print all prime numbers up to `n`.

---

# 27. Final Summary

The Sieve of Eratosthenes is a fast algorithm for finding all primes up to `n`.

The main steps are:

```text
1. Mark 1 as not prime.
2. Start from 2.
3. Select the next uncrossed number as prime.
4. Cross out its multiples.
5. Repeat up to sqrt(n).
6. All remaining uncrossed numbers are prime.
```

For `1` to `100`, we process:

```text
2, 3, 5, 7
```

because:

```text
sqrt(100) = 10
```

The time complexity is:

\[
O(n \log \log n)
\]

The space complexity is:

\[
O(n)
\]

This algorithm is much faster than checking each number separately.
