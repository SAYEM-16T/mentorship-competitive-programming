
# C++ Language Guide for Competitive Programming

This guide covers the **language-level C++ topics** needed for competitive programming, with a **separate STL section**. It is designed so that a beginner can learn the parts of C++ that matter most for problem solving and avoid common language-related mistakes.

---

## Recommended C++ Version

For competitive programming, the best default choice is:

- **GNU++17 / C++17**

Why:

- supported by almost all online judges
- stable STL support
- modern enough for most contest problems
- safer as a default than relying on newer standards everywhere

---

## Main Goal

The goal is to become comfortable enough with C++ that language issues do not block problem solving.

A student should be able to:

- read input and print output confidently
- use conditions and loops correctly
- write and use functions
- work with arrays, strings, and vectors
- understand basic overflow and indexing issues
- use common STL containers and algorithms without confusion

---

# 1. Core C++ Topics for Competitive Programming

---

## 1.1 Input and Output

Learn:

- `cin`
- `cout`
- newline using `"\n"`
- reading multiple values
- printing answers clearly

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int a, b;
    cin >> a >> b;
    cout << a + b << "\n";
    return 0;
}
````

---

## 1.2 Variables and Data Types

The most important data types for CP are:

* `int`
* `long long`
* `char`
* `string`
* `double`
* `bool`

Important rule:

* use `long long` when values or sums/products may become large

```cpp
int a = 100000;
int b = 100000;
// a * b may overflow

long long x = 100000;
long long y = 100000;
cout << x * y << "\n";
```

---

## 1.3 Operators

Learn these operator groups well:

* arithmetic: `+ - * / %`
* comparison: `== != < > <= >=`
* logical: `&& || !`
* assignment: `= += -= *=`
* increment/decrement: `++ --`

---

## 1.4 Conditions

Learn:

* `if`
* `if else`
* `else if`
* nested conditions

```cpp
if (n % 2 == 0) {
    cout << "Even\n";
} else {
    cout << "Odd\n";
}
```

---

## 1.5 Loops

Learn:

* `for`
* `while`
* `break`
* `continue`

```cpp
for (int i = 1; i <= n; i++) {
    cout << i << " ";
}
cout << "\n";
```

---

## 1.6 Functions

Functions are essential in CP.

Learn:

* function declaration
* parameters
* return values
* `void` functions

```cpp
int add(int a, int b) {
    return a + b;
}
```

---

## 1.7 Scope

Understand:

* local variables
* global variables
* function scope

A variable declared inside a function cannot be used outside that function.

---

## 1.8 Standard CP Program Structure

A simple and clean competitive programming template:

```cpp
#include <bits/stdc++.h>
using namespace std;

void solve() {
    int n;
    cin >> n;
    cout << n << "\n";
}

int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);

    solve();
    return 0;
}
```

---

## 1.9 Multiple Test Cases

Many problems use multiple test cases.

```cpp
int t;
cin >> t;
while (t--) {
    solve();
}
```

Important:

* use this only when the problem statement says there are multiple test cases

---

## 1.10 Arrays

Learn:

* declaration
* input/output
* traversal
* finding sum, max, min, count
* reverse traversal

```cpp
int a[100];
for (int i = 0; i < n; i++) cin >> a[i];
```

---

## 1.11 2D Arrays

Basic matrix handling is enough in the beginning.

Learn:

* matrix input
* row-wise traversal
* column-wise traversal

---

## 1.12 Strings

Strings are very common in CP.

Learn:

* input
* length
* indexing
* traversal
* comparison
* reversing

```cpp
string s;
cin >> s;
cout << s.size() << "\n";
cout << s[0] << "\n";
```

---

## 1.13 Characters

Learn:

* `'a'`, `'A'`, `'0'`
* lowercase and uppercase checks
* digit checks

```cpp
char c;
cin >> c;
if (c >= 'a' && c <= 'z') cout << "lowercase\n";
```

---

## 1.14 Pass by Value vs Pass by Reference

This matters for both performance and correctness.

```cpp
void f(vector<int> v) { }      // makes a copy
void g(vector<int>& v) { }     // no copy
```

Good habit:

* pass large vectors/strings by reference when possible

---

## 1.15 `const`

Use `const` when data should not be modified.

```cpp
void print(const vector<int>& v) {
    for (int x : v) cout << x << " ";
}
```

---

## 1.16 Recursion Basics

Learn:

* a function calling itself
* base case
* why missing the base case causes problems

Do not go too deep at the beginning, but basic recursion is useful.

---

## 1.17 Time Complexity Awareness

This is not purely language, but it must be learned alongside C++.

Minimum complexity levels to understand:

* `O(1)`
* `O(log n)`
* `O(n)`
* `O(n log n)`
* `O(n^2)`

Important intuition:

* nested loops are not always safe
* for constraints around `1e5`, `O(n^2)` is often too slow

---

# 2. Essential CP Language Rules

---

## 2.1 Fast I/O

This should be in almost every CP template:

```cpp
ios::sync_with_stdio(false);
cin.tie(nullptr);
```

---

## 2.2 Use `long long` Carefully

Use `long long` when:

* constraints are large
* sum/product can exceed `int`
* prefix sums are involved
* multiplication is used

---

## 2.3 Indexing

Be comfortable with:

* 0-based indexing
* 1-based indexing

Most STL containers use **0-based indexing**.

---

## 2.4 Integer Division

```cpp
cout << 5 / 2 << "\n";   // 2
cout << 5.0 / 2 << "\n"; // 2.5
```

This is a common beginner mistake.

---

## 2.5 Overflow

```cpp
int x = 1e9;
int y = 1e9;
cout << x * y << "\n"; // overflow
```

Safe version:

```cpp
long long ans = 1LL * x * y;
```

---

## 2.6 Floating Point Caution

Avoid direct equality checks with floating point values when possible.

---

## 2.7 Input Differences

* `cin >> s` reads one word
* `getline(cin, s)` reads a full line

This often causes confusion in string problems.

---

# 3. Common C++ Mistakes in Competitive Programming

---

## 3.1 Missing Semicolon

Very common beginner syntax error.

---

## 3.2 `=` vs `==`

```cpp
if (a = 5)   // usually wrong
if (a == 5)  // correct
```

---

## 3.3 Uninitialized Variables

```cpp
int x;
cout << x << "\n"; // garbage value
```

Always initialize when needed.

---

## 3.4 Array Out of Bounds

```cpp
int a[5];
a[5] = 10; // wrong
```

Valid indices are `0` to `4`.

---

## 3.5 Infinite Loop

A loop that never updates its condition correctly can run forever.

---

## 3.6 Off-by-One Errors

Examples:

* `i < n` vs `i <= n`
* starting from `0` vs `1`

Very common in loops and arrays.

---

## 3.7 Wrong Test Case Handling

Do not assume every problem has multiple test cases.

---

# 4. Recommended CP Templates

---

## 4.1 Single Test Case Template

```cpp
#include <bits/stdc++.h>
using namespace std;

using ll = long long;

void solve() {
    int n;
    cin >> n;
    cout << n << "\n";
}

int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);

    solve();
    return 0;
}
```

---

## 4.2 Multiple Test Case Template

```cpp
#include <bits/stdc++.h>
using namespace std;

using ll = long long;

void solve() {
    int n;
    cin >> n;
    cout << n * 2 << "\n";
}

int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);

    int t;
    cin >> t;
    while (t--) solve();

    return 0;
}
```

---

# 5. STL for Competitive Programming

This section is kept separate so STL can be learned as its own toolkit.

---

## 5.1 `vector`

The most important STL container in CP.

Learn:

* declaration
* initialization
* input
* indexing
* loops
* `push_back`
* size
* sorting

```cpp
vector<int> v;
v.push_back(10);
v.push_back(20);

for (int x : v) {
    cout << x << " ";
}
cout << "\n";
```

Important operations:

* `v.push_back(x)`
* `v.pop_back()`
* `v.size()`
* `v.empty()`
* `v.clear()`

Useful initialization:

```cpp
vector<int> v(n);
```

---

## 5.2 `string`

Even though it is often taught early, it is also part of STL.

Useful operations:

* `s.size()`
* `reverse(s.begin(), s.end())`
* `sort(s.begin(), s.end())`

---

## 5.3 `pair`

Stores two values together.

```cpp
pair<int, int> p;
p = {3, 5};
cout << p.first << " " << p.second << "\n";
```

Useful for:

* coordinates
* value + index
* sorting with multiple fields

---

## 5.4 `set`

Stores unique values in sorted order.

```cpp
set<int> st;
st.insert(3);
st.insert(1);
st.insert(3);

for (int x : st) cout << x << " ";
```

Output:

```cpp
1 3
```

Useful operations:

* `insert`
* `erase`
* `find`
* `count`

---

## 5.5 `multiset`

Like `set`, but allows duplicates.

Useful when duplicate values must be stored while keeping sorted order.

---

## 5.6 `map`

Stores key-value pairs sorted by key.

```cpp
map<string, int> mp;
mp["apple"] = 3;
mp["banana"] = 5;

cout << mp["apple"] << "\n";
```

Very useful for:

* frequency counting
* value mapping
* grouping data by key

---

## 5.7 `unordered_map`

Usually faster on average than `map`, but does not keep keys sorted.

Recommended approach:

* learn `map` first
* use `unordered_map` later when comfortable

---

## 5.8 `stack`

Follows LIFO (last in, first out).

```cpp
stack<int> st;
st.push(10);
st.push(20);
cout << st.top() << "\n";
st.pop();
```

---

## 5.9 `queue`

Follows FIFO (first in, first out).

```cpp
queue<int> q;
q.push(10);
q.push(20);
cout << q.front() << "\n";
q.pop();
```

---

## 5.10 `deque`

Double-ended queue.

This is useful, but not essential in the beginning.

---

## 5.11 `priority_queue`

Used for heaps.

### Max Heap

```cpp
priority_queue<int> pq;
pq.push(10);
pq.push(5);
pq.push(20);

cout << pq.top() << "\n"; // 20
```

### Min Heap

```cpp
priority_queue<int, vector<int>, greater<int>> pq;
```

---

# 6. STL Algorithms That Must Be Learned

---

## 6.1 `sort`

```cpp
sort(v.begin(), v.end());
```

Descending order:

```cpp
sort(v.rbegin(), v.rend());
```

---

## 6.2 `reverse`

```cpp
reverse(v.begin(), v.end());
```

---

## 6.3 `min` and `max`

```cpp
cout << min(a, b) << "\n";
cout << max(a, b) << "\n";
```

---

## 6.4 `swap`

```cpp
swap(a, b);
```

---

## 6.5 `count`

```cpp
int c = count(v.begin(), v.end(), 5);
```

---

## 6.6 `find`

```cpp
auto it = find(v.begin(), v.end(), 10);
if (it != v.end()) cout << "Found\n";
```

---

## 6.7 `binary_search`

Requires a sorted container.

```cpp
if (binary_search(v.begin(), v.end(), x)) {
    cout << "YES\n";
}
```

---

## 6.8 `lower_bound`

Returns the first position where `x` can be placed without breaking order.

```cpp
auto it = lower_bound(v.begin(), v.end(), x);
```

---

## 6.9 `upper_bound`

Returns the first position greater than `x`.

```cpp
auto it = upper_bound(v.begin(), v.end(), x);
```

---

## 6.10 `min_element` and `max_element`

```cpp
cout << *min_element(v.begin(), v.end()) << "\n";
cout << *max_element(v.begin(), v.end()) << "\n";
```

---

## 6.11 `accumulate`

```cpp
int sum = accumulate(v.begin(), v.end(), 0);
```

For large sums:

```cpp
long long sum = accumulate(v.begin(), v.end(), 0LL);
```

---

## 6.12 `unique`

Usually used after sorting.

```cpp
sort(v.begin(), v.end());
v.erase(unique(v.begin(), v.end()), v.end());
```

---

## 6.13 `next_permutation`

```cpp
sort(v.begin(), v.end());
do {
    for (int x : v) cout << x << " ";
    cout << "\n";
} while (next_permutation(v.begin(), v.end()));
```

---

# 7. Best Order for Learning STL

Recommended order:

1. `vector`
2. `pair`
3. `sort`
4. string operations
5. `set`
6. `map`
7. `stack`
8. `queue`
9. `priority_queue`
10. `binary_search`, `lower_bound`, `upper_bound`
11. `accumulate`, `count`, `find`, `reverse`, `unique`

---

# 8. STL Topics That Can Wait

These are not necessary at the beginning:

* `deque`
* `list`
* `bitset`
* `unordered_set`
* custom comparators for advanced use
* iterator-heavy tricks

---

# 9. Problem-Solving Checklist for Language Safety

Before submitting a solution, check:

## Input

* should the variables be `int` or `long long`?
* does the problem have multiple test cases?
* is indexing 0-based or 1-based?

## Logic

* does the solution require sorting?
* can overflow happen?
* are negative values possible?
* are edge cases covered?

## Output

* is the output format exact?
* any extra spaces or extra lines?

## Code

* is the array/vector size enough?
* are loop bounds correct?
* is the return type correct?

---

# 10. Language Mastery Milestones

## Level 1

A beginner is comfortable with:

* input/output
* `if/else`
* loops
* functions
* arrays
* strings

## Level 2

A student can start solving many easy CP problems with:

* `vector`
* `pair`
* `sort`
* multiple test cases
* `long long`
* basic complexity awareness

## Level 3

A student becomes safer for easy and many medium problems with:

* `map`
* `set`
* `stack`
* `queue`
* `binary_search`
* `lower_bound`
* `upper_bound`
* prefix sums
* frequency counting

---

# 11. Topics That Can Be Skipped Initially

These are not a priority for early competitive programming:

* OOP and classes
* inheritance
* deep template programming
* deep pointer usage
* file handling
* advanced C-specific features
* advanced macro usage

---

# 12. Minimum C++ Toolkit for Competitive Programming

A student should know the following to avoid most language-related issues.

## Core C++

* `cin/cout`
* `if/else`
* `for/while`
* functions
* arrays
* strings
* `long long`
* multiple test case pattern
* pass by reference basics
* overflow awareness

## STL

* `vector`
* `pair`
* `sort`
* `set`
* `map`
* `stack`
* `queue`
* `priority_queue`
* `binary_search`
* `lower_bound`
* `upper_bound`
* `accumulate`
* `find`
* `count`
* `reverse`
* `unique`

---

# 13. Suggested Learning Path

## Week 1

* input/output
* variables
* operators
* `if/else`
* loops
* functions

## Week 2

* arrays
* strings
* multiple test cases
* `long long`
* debugging basics

## Week 3

* `vector`
* `pair`
* `sort`
* `reverse`
* `find`
* `count`

## Week 4

* `set`
* `map`
* frequency counting
* `binary_search`
* `lower_bound`
* `upper_bound`

## Week 5

* `stack`
* `queue`
* `priority_queue`
* common STL-based problems

---
