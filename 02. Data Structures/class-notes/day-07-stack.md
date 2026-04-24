# Stack — Teaching Plan & Competitive Programming Notes

**Course context:** ICT 2101 Data Structures — Stack: Introduction, stack operations (`push`, `pop`), stack implementation, and stack applications.  
**CP focus:** problem-solving patterns where Last-In-First-Out (LIFO) behavior gives an efficient solution.

---

## 1. Learning Outcomes

After this module, students should be able to:

1. Explain Stack as an Abstract Data Type (ADT).
2. Identify LIFO behavior in real-life and programming problems.
3. Implement Stack using:
   - Array / static array
   - Dynamic array / `vector`
   - Linked list
   - STL `stack`
4. Analyze time and space complexity of stack operations.
5. Apply stack in competitive programming problems:
   - Balanced parentheses
   - Next Greater / Smaller Element
   - Monotonic Stack
   - Expression conversion/evaluation
   - DFS simulation
   - Histogram / rectangle problems
   - Undo-style state tracking

---

## 2. Prerequisites

Students should already know:

- Basic C/C++ syntax
- Array and pointer basics
- Functions and loops
- Basic complexity: `O(1)`, `O(n)`, `O(n log n)`
- Linked list basics, if linked-list stack is covered

---

## 3. Core Concept: What is a Stack?

A **Stack** is a linear data structure where insertion and deletion happen from one side only, called the **top**.

### Rule

> Last In, First Out — **LIFO**

The last element inserted is the first element removed.

### Real-life examples

- Stack of plates
- Browser back button
- Undo operation in editor
- Recursion call stack
- Function calls

---

## 4. Stack ADT Operations

| Operation | Meaning | Complexity |
|---|---|---|
| `push(x)` | Insert `x` at top | `O(1)` |
| `pop()` | Remove top element | `O(1)` |
| `top()` / `peek()` | Return top element | `O(1)` |
| `empty()` | Check if stack has no element | `O(1)` |
| `size()` | Number of elements | `O(1)` if maintained |

### Important edge cases

- Pop from empty stack → underflow
- Top from empty stack → invalid access
- Push into full fixed-size array stack → overflow

---

## 5. Stack Implementation Using Array

### Idea

Maintain an integer `topIndex`.

- Initially `topIndex = -1`
- `push(x)` → increment `topIndex`, assign value
- `pop()` → decrement `topIndex`
- `top()` → `arr[topIndex]`

### C++ Code

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
        arr[++topIndex] = x;
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
    cout << st.top() << "\n"; // 20
    st.pop();
    cout << st.top() << "\n"; // 10
}
```

---

## 6. Stack Implementation Using `vector`

For competitive programming, `vector` is often easier.

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
        if (!v.empty()) v.pop_back();
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

## 7. Stack Using STL

In competitive programming, use this most of the time.

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    stack<int> st;

    st.push(5);
    st.push(10);

    cout << st.top() << "\n"; // 10

    st.pop();

    cout << st.top() << "\n"; // 5
}
```

### STL Stack common functions

| Function | Use |
|---|---|
| `st.push(x)` | Insert |
| `st.pop()` | Remove top, does not return value |
| `st.top()` | Access top |
| `st.empty()` | Check empty |
| `st.size()` | Size |

### Common CP warning

`pop()` does not return the top element.  
Use:

```cpp
int x = st.top();
st.pop();
```

---

## 8. Linked List Stack

### Idea

The head of linked list acts as stack top.

```cpp
#include <bits/stdc++.h>
using namespace std;

struct Node {
    int data;
    Node* next;

    Node(int value) {
        data = value;
        next = nullptr;
    }
};

class StackLinkedList {
private:
    Node* topNode;

public:
    StackLinkedList() {
        topNode = nullptr;
    }

    bool empty() {
        return topNode == nullptr;
    }

    void push(int x) {
        Node* newNode = new Node(x);
        newNode->next = topNode;
        topNode = newNode;
    }

    void pop() {
        if (empty()) {
            cout << "Stack Underflow\n";
            return;
        }
        Node* temp = topNode;
        topNode = topNode->next;
        delete temp;
    }

    int top() {
        if (empty()) {
            cout << "Stack is empty\n";
            return -1;
        }
        return topNode->data;
    }
};
```

### Discussion point

Array stack has fixed capacity unless dynamic.  
Linked list stack grows dynamically but uses extra memory for pointers.

---

## 9. Application 1: Balanced Parentheses

### Problem

Given a string containing brackets `()`, `{}`, `[]`, determine whether it is balanced.

### Pattern

Use stack to store opening brackets.

### Code

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

    cout << (isBalanced(s) ? "YES" : "NO") << "\n";
}
```

### Complexity

- Time: `O(n)`
- Space: `O(n)`

### CP Problems

- HackerRank: Balanced Brackets
- LeetCode 20: Valid Parentheses
- LightOJ / Codeforces bracket sequence problems

---

## 10. Application 2: Next Greater Element

### Problem

For each element, find the next element on the right that is greater.

Example:

```text
Input:  2 1 5 3
Output: 5 5 -1 -1
```

### Naive solution

For each index, scan right side → `O(n^2)`

### Stack solution

Use a **monotonic decreasing stack**.

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;

    vector<int> a(n), ans(n, -1);
    for (int i = 0; i < n; i++) cin >> a[i];

    stack<int> st; // stores indices

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

### Complexity

- Time: `O(n)`
- Space: `O(n)`

Each element is pushed once and popped once.

---

## 11. Monotonic Stack

A **monotonic stack** maintains elements in increasing or decreasing order.

### When to use

Look for phrases like:

- Next greater element
- Previous greater element
- Next smaller element
- Previous smaller element
- Nearest greater/smaller
- Remove elements while condition holds
- Largest rectangle in histogram

### Template: Next Smaller Element

```cpp
vector<int> nextSmaller(vector<int>& a) {
    int n = a.size();
    vector<int> ans(n, -1);
    stack<int> st;

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

## 12. Application 3: Largest Rectangle in Histogram

### Problem idea

Given heights of bars, find the largest rectangle area.

### Key concept

For each bar, find:

- Previous smaller element
- Next smaller element

Then width can be calculated.

### CP importance

This is one of the most important stack problems.

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

## 13. Application 4: Expression Evaluation

Stack is used for:

- Infix to postfix conversion
- Postfix evaluation
- Prefix evaluation
- Operator precedence handling

### Postfix evaluation example

Expression: `2 3 + 4 *`

Meaning: `(2 + 3) * 4 = 20`

```cpp
#include <bits/stdc++.h>
using namespace std;

int evaluatePostfix(vector<string> tokens) {
    stack<int> st;

    for (string token : tokens) {
        if (token == "+" || token == "-" || token == "*" || token == "/") {
            int b = st.top(); st.pop();
            int a = st.top(); st.pop();

            if (token == "+") st.push(a + b);
            else if (token == "-") st.push(a - b);
            else if (token == "*") st.push(a * b);
            else st.push(a / b);
        } else {
            st.push(stoi(token));
        }
    }

    return st.top();
}
```

---

## 14. Application 5: DFS Using Stack

Recursive DFS internally uses call stack.  
We can also implement DFS iteratively using stack.

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n, m;
    cin >> n >> m;

    vector<vector<int>> graph(n + 1);

    for (int i = 0; i < m; i++) {
        int u, v;
        cin >> u >> v;
        graph[u].push_back(v);
        graph[v].push_back(u);
    }

    vector<bool> visited(n + 1, false);
    stack<int> st;

    st.push(1);
    visited[1] = true;

    while (!st.empty()) {
        int node = st.top();
        st.pop();

        cout << node << " ";

        for (int child : graph[node]) {
            if (!visited[child]) {
                visited[child] = true;
                st.push(child);
            }
        }
    }
}
```

---

## 15. Teaching Flow

### Class 1: Concept + Basic Implementation

1. Explain LIFO with examples.
2. Demonstrate `push`, `pop`, `top`.
3. Draw stack state after each operation.
4. Implement using array.
5. Discuss overflow and underflow.

### Class 2: STL + CP Problems

1. Introduce `stack<int>`.
2. Solve balanced parentheses.
3. Solve next greater element.
4. Explain monotonic stack.

### Class 3: Advanced Stack Applications

1. Largest rectangle in histogram.
2. Expression evaluation.
3. Iterative DFS.
4. Practice contest.

---

## 16. Classroom Demonstration

Given operations:

```text
push(10)
push(20)
push(30)
pop()
push(40)
top()
```

Final stack:

```text
Top -> 40
       20
       10
```

Output of `top()` is `40`.

---

## 17. Common Mistakes

1. Calling `top()` when stack is empty.
2. Thinking `pop()` returns value.
3. Forgetting to pop inside `while`.
4. Confusing stack with queue.
5. Using stack when order should be FIFO.
6. In monotonic stack, storing values when indices are needed.
7. Not handling duplicate values properly.

---

## 18. CP Pattern Recognition

Use stack when:

- Recent previous element matters.
- You need to reverse order.
- Matching pairs are involved.
- Nested structure exists.
- You need nearest greater/smaller element.
- Recursion can be simulated.
- You need undo/backtracking behavior.

---

## 19. Practice Problems

### Beginner

1. Implement stack using array.
2. Implement stack using linked list.
3. Reverse a string using stack.
4. Check balanced parentheses.
5. Remove adjacent duplicate characters.

### Intermediate

1. Next Greater Element
2. Next Smaller Element
3. Previous Greater Element
4. Previous Smaller Element
5. Stock Span Problem
6. Min Stack
7. Queue using two stacks

### Advanced

1. Largest Rectangle in Histogram
2. Maximal Rectangle in Binary Matrix
3. Remove K Digits
4. Decode String
5. Asteroid Collision
6. Sum of Subarray Minimums
7. Basic Calculator

### Suggested online platforms

- Codeforces
- LeetCode
- HackerRank
- CSES
- AtCoder
- LightOJ

---

## 20. Mini Contest Plan

Duration: 90 minutes

| Problem | Topic | Difficulty |
|---|---|---|
| A | Stack implementation | Easy |
| B | Balanced brackets | Easy |
| C | Next greater element | Medium |
| D | Stock span | Medium |
| E | Histogram rectangle | Hard |

---

## 21. Assignment

1. Implement stack using array and linked list.
2. Compare both implementations.
3. Solve at least 5 stack CP problems.
4. Write complexity analysis for each solution.
5. Explain one real-life application of stack.

---

## 22. Quick Revision Sheet

- Stack follows LIFO.
- `push`, `pop`, `top` are `O(1)`.
- STL stack is best for CP unless custom behavior is needed.
- Monotonic stack solves nearest greater/smaller problems in `O(n)`.
- Always check `empty()` before `top()` or `pop()`.
- Use stack for brackets, recursion simulation, expression problems, and nested structures.