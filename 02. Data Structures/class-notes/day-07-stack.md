# Stack — Student Teaching Note + CP Practice

**Topic:** Stack in C++

---

## 1. Stack কী?

**Stack** হলো এমন একটি linear data structure যেখানে data ঢোকানো এবং বের করা হয় একই দিক থেকে। এই দিককে বলা হয় **top**।

Stack-এর main rule:

> **LIFO = Last In, First Out**

মানে, যে element সবার শেষে ঢুকেছে, সে-ই সবার আগে বের হবে।

### ছোট example

```text
push(10)
push(20)
push(30)
```

তাহলে stack হবে:

```text
Top -> 30
       20
       10
```

এখন `pop()` করলে 30 বের হবে, কারণ 30 সবার শেষে ঢুকেছিল।

---

## 2. Real-life analogy

Stack বোঝানোর জন্য কয়েকটা easy analogy:

### 1. Plate stack

বিয়ের অনুষ্ঠানে plate একটার উপর একটা রাখা থাকে।

```text
Top plate -> সবার আগে নেওয়া যায়
Bottom plate -> আগে নেওয়া যায় না
```

শেষে রাখা plate আগে নেওয়া হয়। তাই এটি LIFO।

### 2. Browser back button

তুমি browser-এ visit করলে:

```text
Google -> YouTube -> Codeforces -> AtCoder
```

Back চাপলে আগে AtCoder থেকে Codeforces-এ যাবে। শেষ page আগে বের হয়।

### 3. Undo operation

Editor-এ কাজ করলে:

```text
Type A
Type B
Type C
```

Undo করলে আগে C remove হবে, তারপর B, তারপর A।

### 4. Recursion call stack

Function call করলে computer internally stack use করে।

```cpp
fun1() calls fun2()
fun2() calls fun3()
```

প্রথমে `fun3()` শেষ হবে, তারপর `fun2()`, তারপর `fun1()`।

---

## 3. Stack operations

| Operation          | Meaning                    | Time Complexity |
| ------------------ | -------------------------- | --------------- |
| `push(x)`          | top এ x insert করে         | `O(1)`          |
| `pop()`            | top element remove করে     | `O(1)`          |
| `top()` / `peek()` | top element দেখায়          | `O(1)`          |
| `empty()`          | stack empty কিনা check করে | `O(1)`          |
| `size()`           | stack এ কয়টা element আছে   | `O(1)`          |

### Important warning

C++ STL stack-এ `pop()` value return করে না।

ভুল:

```cpp
int x = st.pop(); // wrong
```

সঠিক:

```cpp
int x = st.top();
st.pop();
```

আর `top()` বা `pop()` করার আগে অবশ্যই `empty()` check করতে হবে।

```cpp
if (!st.empty()) {
    cout << st.top() << "\n";
    st.pop();
}
```

---

## 4. C++ STL Stack

Competitive programming-এ সাধারণত STL stack use করাই best।

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    stack<int> st;

    st.push(10);
    st.push(20);
    st.push(30);

    cout << st.top() << "\n"; // 30

    st.pop();

    cout << st.top() << "\n"; // 20
    cout << st.size() << "\n"; // 2
    cout << st.empty() << "\n"; // 0 means false

    return 0;
}
```

---

## 5. Manual stack implementation using array

Stack internally কীভাবে কাজ করে সেটা বোঝানোর জন্য array implementation দেখানো ভালো।

### Idea

আমরা একটা variable রাখব: `topIndex`।

* শুরুতে `topIndex = -1`
* `push(x)` করলে `topIndex++`, তারপর value রাখব
* `pop()` করলে `topIndex--`
* `top()` মানে `arr[topIndex]`

```cpp
#include <bits/stdc++.h>
using namespace std;

class StackArray {
private:
    int arr[1000];
    int topIndex;

public:
    StackArray() {
        topIndex = -1;
    }

    bool empty() {
        return topIndex == -1;
    }

    bool full() {
        return topIndex == 999;
    }

    void push(int x) {
        if (full()) {
            cout << "Stack Overflow\n";
            return;
        }
        topIndex++;
        arr[topIndex] = x;
    }

    void pop() {
        if (empty()) {
            cout << "Stack Underflow\n";
            return;
        }
        topIndex--;
    }

    int top() {
        if (empty()) {
            cout << "Stack is empty\n";
            return -1;
        }
        return arr[topIndex];
    }

    int size() {
        return topIndex + 1;
    }
};

int main() {
    StackArray st;
    st.push(10);
    st.push(20);
    st.push(30);

    cout << st.top() << "\n"; // 30
    st.pop();
    cout << st.top() << "\n"; // 20
}
```

---

## 6. Stack using vector

Array fixed size হলে overflow হতে পারে। `vector` dynamic হওয়ায় CP-তে অনেক সময় useful।

```cpp
#include <bits/stdc++.h>
using namespace std;

class StackVector {
private:
    vector<int> v;

public:
    void push(int x) {
        v.push_back(x);
    }

    void pop() {
        if (!v.empty()) {
            v.pop_back();
        }
    }

    int top() {
        return v.back();
    }

    bool empty() {
        return v.empty();
    }

    int size() {
        return (int)v.size();
    }
};
```

---

## 7. Classroom dry run

Operations:

```text
push(10)
push(20)
push(30)
pop()
push(40)
top()
```

Step by step:

```text
push(10): 10
push(20): 20, 10
push(30): 30, 20, 10
pop():    20, 10
push(40): 40, 20, 10
top():    40
```

Final stack:

```text
Top -> 40
       20
       10
```

Output of `top()` is `40`.

---

## 8. Application 1: Balanced Parentheses

### Problem idea

String দেওয়া আছে। Check করতে হবে brackets balanced কিনা।

Balanced:

```text
()[]{}
({[]})
```

Not balanced:

```text
([)]
(()
])
```

### Stack idea

* Opening bracket পেলে stack-এ push করব।
* Closing bracket পেলে stack-এর top এর সাথে match করব।
* Match হলে pop করব।
* শেষে stack empty হলে balanced।

```cpp
#include <bits/stdc++.h>
using namespace std;

bool isBalanced(string s) {
    stack<char> st;

    for (char c : s) {
        if (c == '(' || c == '{' || c == '[') {
            st.push(c);
        } else {
            if (st.empty()) return false;

            char top = st.top();
            st.pop();

            if (c == ')' && top != '(') return false;
            if (c == '}' && top != '{') return false;
            if (c == ']' && top != '[') return false;
        }
    }

    return st.empty();
}

int main() {
    string s;
    cin >> s;

    if (isBalanced(s)) cout << "YES\n";
    else cout << "NO\n";
}
```

Complexity:

```text
Time:  O(n)
Space: O(n)
```

---

## 9. Application 2: Backspace / Undo style problem

ধরো string-এ `B` মানে backspace।

Input:

```text
01B0
```

Process:

```text
0
01
0      // B pressed, last char removed
00
```

Final answer:

```text
00
```

Stack idea:

* Normal char হলে push
* Backspace হলে pop

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    string s;
    cin >> s;

    string st;

    for (char c : s) {
        if (c == 'B') {
            if (!st.empty()) st.pop_back();
        } else {
            st.push_back(c);
        }
    }

    cout << st << "\n";
}
```

Note: এখানে `string`-কেই stack এর মতো use করা হয়েছে। `push_back()` হলো push, `pop_back()` হলো pop।

---

## 10. Application 3: Remove adjacent duplicate / cancellation

অনেক problem-এ বলা থাকে পাশের দুইটা same হলে remove হবে।

Example:

```text
abbaca
```

Process:

```text
abbaca -> aaca -> ca
```

Stack idea:

* Current char যদি stack top এর equal হয়, top pop।
* না হলে current char push।

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    string s;
    cin >> s;

    string st;

    for (char c : s) {
        if (!st.empty() && st.back() == c) {
            st.pop_back();
        } else {
            st.push_back(c);
        }
    }

    cout << st << "\n";
}
```

---

## 11. Application 4: Next Greater Element

### Problem

প্রতিটি element-এর ডান পাশে প্রথম বড় element বের করতে হবে।

Example:

```text
Input:  2 1 5 3
Output: 5 5 -1 -1
```

### Naive idea

প্রতিটি index থেকে right side scan করলে `O(n^2)`।

### Stack idea

Monotonic stack use করলে `O(n)`।

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;

    vector<int> a(n), ans(n, -1);
    for (int i = 0; i < n; i++) cin >> a[i];

    stack<int> st; // index store করব

    for (int i = 0; i < n; i++) {
        while (!st.empty() && a[i] > a[st.top()]) {
            ans[st.top()] = a[i];
            st.pop();
        }
        st.push(i);
    }

    for (int x : ans) cout << x << " ";
    cout << "\n";
}
```

Why `O(n)`?

প্রতিটি element stack-এ একবার push হয় এবং সর্বোচ্চ একবার pop হয়। তাই total কাজ `O(n)`।

---

## 12. Monotonic Stack pattern

**Monotonic stack** এমন stack যেখানে elements increasing/decreasing order maintain করে রাখা হয়।

এই phrase গুলো দেখলে stack ভাববে:

* next greater element
* next smaller element
* previous greater element
* previous smaller element
* nearest greater/smaller
* first greater/smaller on left/right
* remove while condition true
* largest rectangle in histogram

### Template: Next Smaller Element

```cpp
vector<int> nextSmaller(vector<int>& a) {
    int n = a.size();
    vector<int> ans(n, -1);
    stack<int> st; // index store

    for (int i = 0; i < n; i++) {
        while (!st.empty() && a[i] < a[st.top()]) {
            ans[st.top()] = a[i];
            st.pop();
        }
        st.push(i);
    }

    return ans;
}
```

---

## 13. Advanced Application: Largest Rectangle in Histogram

এই problem advanced, কিন্তু stack শেখানোর জন্য খুব important।

### Main idea

প্রতিটি bar-এর জন্য জানতে হবে:

* left side-এ previous smaller কোথায়
* right side-এ next smaller কোথায়

তাহলে ঐ bar height ধরে maximum width বের করা যায়।

```cpp
#include <bits/stdc++.h>
using namespace std;

long long largestRectangleArea(vector<int>& h) {
    int n = h.size();
    stack<int> st;
    long long best = 0;

    for (int i = 0; i <= n; i++) {
        int currentHeight = (i == n ? 0 : h[i]);

        while (!st.empty() && currentHeight < h[st.top()]) {
            int height = h[st.top()];
            st.pop();

            int leftSmallerIndex = st.empty() ? -1 : st.top();
            int width = i - leftSmallerIndex - 1;

            best = max(best, 1LL * height * width);
        }

        st.push(i);
    }

    return best;
}

int main() {
    int n;
    cin >> n;

    vector<int> h(n);
    for (int i = 0; i < n; i++) cin >> h[i];

    cout << largestRectangleArea(h) << "\n";
}
```

---

## 14. Common mistakes

1. Empty stack হলে `top()` call করা।
2. Empty stack হলে `pop()` call করা।
3. মনে করা `pop()` value return করে।
4. Stack আর queue confuse করা।
5. Monotonic stack-এ value store করা, কিন্তু problem-এর জন্য index দরকার ছিল।
6. Duplicate value handle না করা।
7. `while` এর জায়গায় ভুল করে `if` use করা।
8. Bracket matching-এ closing bracket আসলে empty check না করা।

---

## 15. Stack vs Queue quick difference

| Topic   | Stack        | Queue        |
| ------- | ------------ | ------------ |
| Rule    | LIFO         | FIFO         |
| Insert  | top          | back/rear    |
| Remove  | top          | front        |
| Analogy | plate stack  | line/queue   |
| C++ STL | `stack<int>` | `queue<int>` |

---

## 16. Teaching flow

### Class 1: Concept + Basic Operations

1. Plate analogy দিয়ে LIFO explain.
2. `push`, `pop`, `top`, `empty`, `size` বোঝানো।
3. Board-এ stack dry run।
4. Array implementation দেখানো।
5. Overflow/underflow explain।

### Class 2: STL + Easy CP Pattern

1. `stack<int>` and `stack<char>` use।
2. Balanced parentheses solve।
3. Backspace/undo problem solve।
4. Adjacent duplicate cancellation।

### Class 3: Monotonic Stack

1. Next greater element naive `O(n^2)` explain।
2. Stack solution `O(n)` explain।
3. Next smaller template।
4. Practice problem discussion।

### Class 4: Advanced

1. Histogram rectangle।
2. Mixed bracket replacement।
3. Contest-style practice।

---

## 17. 12 Practice Problems — 4 each from Codeforces, AtCoder, CodeChef

### Codeforces — 4 problems

| # | Problem                                                    | Level       | Stack pattern                                 |
| - | ---------------------------------------------------------- | ----------- | --------------------------------------------- |
| 1 | Codeforces 343B — Alternating Current                      | Easy        | adjacent cancellation using stack             |
| 2 | Codeforces 1104B — Game with string                        | Easy-Medium | remove adjacent equal characters, count moves |
| 3 | Codeforces 612C — Replace To Make Regular Bracket Sequence | Medium      | bracket matching + replacement count          |
| 4 | Codeforces 5C — Longest Regular Bracket Sequence           | Medium-Hard | longest valid bracket substring               |

Links:

* [https://codeforces.com/problemset/problem/343/B](https://codeforces.com/problemset/problem/343/B)
* [https://codeforces.com/problemset/problem/1104/B](https://codeforces.com/problemset/problem/1104/B)
* [https://codeforces.com/problemset/problem/612/C](https://codeforces.com/problemset/problem/612/C)
* [https://codeforces.com/problemset/problem/5/C](https://codeforces.com/problemset/problem/5/C)

### AtCoder — 4 problems

| # | Problem                            | Level       | Stack pattern                                           |
| - | ---------------------------------- | ----------- | ------------------------------------------------------- |
| 1 | AtCoder ABC043 B — Unhappy Hacking | Easy        | backspace simulation                                    |
| 2 | AtCoder ABC120 C — Unification     | Easy-Medium | remove adjacent different characters / stack simulation |
| 3 | AtCoder ABC240 D — Strange Balls   | Medium      | stack of pairs, frequency tracking                      |
| 4 | AtCoder ABC328 D — Take ABC        | Medium      | remove substring using stack/string                     |

Links:

* [https://atcoder.jp/contests/abc043/tasks/abc043_b](https://atcoder.jp/contests/abc043/tasks/abc043_b)
* [https://atcoder.jp/contests/abc120/tasks/abc120_c](https://atcoder.jp/contests/abc120/tasks/abc120_c)
* [https://atcoder.jp/contests/abc240/tasks/abc240_d](https://atcoder.jp/contests/abc240/tasks/abc240_d)
* [https://atcoder.jp/contests/abc328/tasks/abc328_d](https://atcoder.jp/contests/abc328/tasks/abc328_d)

### CodeChef — 4 problems

| # | Problem                                           | Level  | Stack pattern        |
| - | ------------------------------------------------- | ------ | -------------------- |
| 1 | CodeChef STACK08 — Stack Introduction             | Easy   | basic stack concept  |
| 2 | CodeChef STACK05 — Valid Parenthesis              | Easy   | balanced parentheses |
| 3 | CodeChef STACT10 — Next Greater Element Algorithm | Medium | monotonic stack      |
| 4 | CodeChef STACK14 — Next Smaller Element           | Medium | monotonic stack      |

Links:

* [https://www.codechef.com/learn/course/stacks-and-queues/LSTACKS/problems/STACK08](https://www.codechef.com/learn/course/stacks-and-queues/LSTACKS/problems/STACK08)
* [https://www.codechef.com/learn/course/stacks-and-queues/LSTACKS02/problems/STACK05](https://www.codechef.com/learn/course/stacks-and-queues/LSTACKS02/problems/STACK05)
* [https://www.codechef.com/learn/course/stacks-and-queues/LSTACKS02/problems/STACT10](https://www.codechef.com/learn/course/stacks-and-queues/LSTACKS02/problems/STACT10)
* [https://www.codechef.com/learn/course/stacks-and-queues/LSTACKS02/problems/STACK14](https://www.codechef.com/learn/course/stacks-and-queues/LSTACKS02/problems/STACK14)

---

## 18. Suggested order for students

Students যেন easy থেকে hard order-এ solve করে:

1. CodeChef STACK08 — Stack Introduction
2. AtCoder ABC043 B — Unhappy Hacking
3. CodeChef STACK05 — Valid Parenthesis
4. Codeforces 343B — Alternating Current
5. AtCoder ABC120 C — Unification
6. Codeforces 1104B — Game with string
7. CodeChef STACT10 — Next Greater Element Algorithm
8. CodeChef STACK14 — Next Smaller Element
9. AtCoder ABC240 D — Strange Balls
10. AtCoder ABC328 D — Take ABC
11. Codeforces 612C — Replace To Make Regular Bracket Sequence
12. Codeforces 5C — Longest Regular Bracket Sequence

---

## 19. Mini contest plan

Duration: 90 minutes

| Problem | Topic                 | Difficulty  |
| ------- | --------------------- | ----------- |
| A       | Basic stack operation | Easy        |
| B       | Backspace simulation  | Easy        |
| C       | Balanced parentheses  | Easy-Medium |
| D       | Adjacent cancellation | Medium      |
| E       | Next greater element  | Medium      |

---

## 20. Final revision

* Stack follows **LIFO**.
* `push`, `pop`, `top`, `empty`, `size` are main operations.
* `push`, `pop`, `top` usually `O(1)`।
* C++ STL stack-এ `pop()` value return করে না।
* Always check `empty()` before `top()` or `pop()`।
* Bracket matching, undo/backspace, recursion, expression evaluation, DFS simulation, next greater/smaller — এসব জায়গায় stack লাগে।
* Monotonic stack শেখা CP-র জন্য very important।

---

## 21. Homework

1. Stack using array implement করো।
2. Stack using vector implement করো।
3. Balanced parentheses solve করো।
4. Next greater element solve করো।
5. Practice list থেকে minimum 5টা problem solve করো।
6. প্রতিটা solution-এর time and space complexity লিখো।
