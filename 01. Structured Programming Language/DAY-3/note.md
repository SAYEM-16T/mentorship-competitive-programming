# Class Note: Vector, Sort, Binary Search, Pair, Stack, Queue

আজকের class-এর main goal হলো:

* আগের basic জিনিসগুলো একটু revise করা
* time complexity বুঝা
* `vector` শেখা
* `sort()` ব্যবহার করা
* simple `binary search` শেখা
* `pair` শেখা
* `stack` basic operations শেখা
* `queue` basic operations শেখা

---

# 1. Quick Revision

নতুন topic-এ যাওয়ার আগে নিচের basic জিনিসগুলো clear থাকতে হবে।

## 1.1 Revision Questions

1. `int`, `double`, `char`, `string` — এদের কাজ কী?
2. `if-else` কখন use করা হয়?
3. `for` loop আর `while` loop-এর basic difference কী?
4. Array কী?
5. `break` কী করে?
6. `continue` কী করে?
7. একটা number even না odd কিভাবে check করা যায়?
8. Array-এর সব element print করতে loop কেন লাগে?
9. Array-এর maximum value কিভাবে বের করা যায়?
10. String-এর first character কিভাবে access করা যায়?

---

## 1.2 Quick Revision Example

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;                         // number of elements

    int a[100];                       // declare an array

    for (int i = 0; i < n; i++) {
        cin >> a[i];                  // input array elements
    }

    int sum = 0;                      // variable to store total sum

    for (int i = 0; i < n; i++) {
        sum += a[i];                  // add each element to sum
    }

    cout << sum << "\n";              // print total sum
    return 0;
}
```

---

# 2. Time Complexity

Time complexity দিয়ে বোঝা যায় input size বাড়লে program কত fast বা কত slow হবে।

আমরা exact second measure করি না।
আমরা দেখি algorithm input বড় হলে কেমন behave করে।

---

## 2.1 Common Time Complexities

### `O(1)`

একটা fixed কাজ।

Example:

* নির্দিষ্ট index access করা

```cpp
int a[5] = {10, 20, 30, 40, 50};
cout << a[2] << "\n";   // direct access
```

---

### `O(n)`

সব element একবার করে দেখা।

```cpp
for (int i = 0; i < n; i++) {
    cout << a[i] << " ";
}
```

---

### `O(n^2)`

সাধারণত nested loop।

```cpp
for (int i = 0; i < n; i++) {
    for (int j = 0; j < n; j++) {
        cout << i << " " << j << "\n";
    }
}
```

---

### `O(log n)`

প্রতিবার search space অর্ধেক হয়ে যায়।

Example:

* binary search

---

### `O(n log n)`

Common example:

* sorting

---

## 2.2 Time Complexity Examples

### Example 1

```cpp
for (int i = 0; i < n; i++) {
    cout << a[i] << "\n";
}
```

Complexity: **`O(n)`**

### Example 2

```cpp
for (int i = 0; i < n; i++) {
    for (int j = 0; j < n; j++) {
        cout << a[i] + a[j] << "\n";
    }
}
```

Complexity: **`O(n^2)`**

### Example 3

```cpp
cout << a[3] << "\n";
```

Complexity: **`O(1)`**

### Example 4

```cpp
sort(v.begin(), v.end());
```

Complexity: **`O(n log n)`**

### Example 5

Binary search:

```cpp
while (left <= right) {
    int mid = (left + right) / 2;
    ...
}
```

Complexity: **`O(log n)`**

---

## 2.3 Important Idea

* Linear Search → `O(n)`
* Binary Search → `O(log n)`
* Sort → `O(n log n)`

এই comparison খুব important।
কারণ efficient problem solving-এর জন্য fast approach চিনতে হবে।

---

# 3. Vector

`vector` হলো dynamic array।

এর মানে:

* size আগে থেকে fix করতে হয় না
* পরে element add করা যায়
* CP-তে খুব বেশি use হয়

---

## 3.1 Why Vector?

Array-এর problem:

* size fixed
* new element easily add করা যায় না

Vector-এর advantage:

* `push_back()` দিয়ে element add করা যায়
* `size()` দিয়ে size জানা যায়
* indexing করা যায়
* STL algorithm-এর সাথে use করা যায়

---

## 3.2 Basic Vector Declaration

```cpp
vector<int> v;
```

এটা একটি empty integer vector তৈরি করে।

---

## 3.3 Full Vector Demo Code

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> v;                            // create an empty vector

    v.push_back(10);                          // add 10 at the end
    v.push_back(20);                          // add 20 at the end
    v.push_back(30);                          // add 30 at the end

    cout << v.size() << "\n";                // print current size

    cout << v[0] << "\n";                    // print first element
    cout << v[1] << "\n";                    // print second element

    v.pop_back();                            // remove last element

    cout << v.size() << "\n";                // print new size

    if (v.empty()) {                         // check if vector is empty
        cout << "Vector is empty\n";
    } else {
        cout << "Vector is not empty\n";
    }

    for (int i = 0; i < v.size(); i++) {     // print vector using loop
        cout << v[i] << " ";
    }
    cout << "\n";

    return 0;
}
```

---

## 3.4 Vector of Fixed Size

```cpp
vector<int> a(5);    // creates a vector of size 5
```

---

## 3.5 Input and Output with Vector

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;                                // input size

    vector<int> v(n);                        // create vector of size n

    for (int i = 0; i < n; i++) {
        cin >> v[i];                         // input vector elements
    }

    for (int i = 0; i < n; i++) {
        cout << v[i] << " ";                 // print vector elements
    }
    cout << "\n";

    return 0;
}
```

---

## 3.6 Important Vector Operations

* `vector<int> v;`
* `vector<int> v(n);`
* `v.push_back(x);`
* `v.pop_back();`
* `v.size();`
* `v.empty();`
* `v[i]`

---

## 3.7 Small Vector Practice

1. Input `n`, then input `n` numbers into a vector and print them.
2. Find sum of all elements.
3. Count even numbers.
4. Find maximum value.
5. Print elements in reverse order.

---

# 4. Sort

Sorting মানে data-কে order অনুযায়ী সাজানো।

---

## 4.1 Ascending Sort

```cpp
sort(v.begin(), v.end());
```

এতে ছোট থেকে বড় order হবে।

---

## 4.2 Descending Sort

```cpp
sort(v.rbegin(), v.rend());
```

এতে বড় থেকে ছোট order হবে।

---

## 4.3 Sort Example

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> v = {5, 2, 9, 1, 7};

    sort(v.begin(), v.end());               // sort in ascending order

    for (int x : v) {
        cout << x << " ";                   // print sorted elements
    }
    cout << "\n";

    return 0;
}
```

---

## 4.4 Important Note About Sort

আজকের জন্য `sort()`-কে **black box** হিসেবে ধরে নিলেও সমস্যা নেই।

শুধু মনে রাখতে হবে:

* এটা fast
* CP-তে খুব useful
* complexity সাধারণত **`O(n log n)`**
* ভেতরে কিভাবে কাজ করে সেটা পরে detail-এ দেখা যাবে

---

## 4.5 Sort Practice

1. Input numbers and print them sorted.
2. Print smallest and largest value.
3. Print second largest value.
4. Sort in descending order.

---

# 5. Simple Binary Search

Binary search use করা হয় **sorted array/vector**-এ কোনো target value আছে কি না বের করতে।

---

## 5.1 Main Idea

প্রতিবার middle element check করা হয়।

* middle == target → found
* middle < target → right half-এ search
* middle > target → left half-এ search

তাই search space অর্ধেক হয়ে যায়।

এই কারণেই complexity:

* **`O(log n)`**

---

## 5.2 Important Rule

**Binary Search only works on sorted data.**

---

## 5.3 Manual Binary Search Code

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> v = {1, 3, 5, 7, 9, 11, 13};   // sorted vector
    int target = 7;                            // value to search

    int left = 0;                              // first index
    int right = v.size() - 1;                  // last index
    bool found = false;                        // flag

    while (left <= right) {
        int mid = (left + right) / 2;          // middle index

        if (v[mid] == target) {                // found target
            found = true;
            break;
        } else if (v[mid] < target) {          // search right half
            left = mid + 1;
        } else {                               // search left half
            right = mid - 1;
        }
    }

    if (found) {
        cout << "Found\n";
    } else {
        cout << "Not Found\n";
    }

    return 0;
}
```

---

## 5.4 Binary Search Practice

1. Given a sorted vector, check if `x` exists.
2. Print `YES` if found, otherwise `NO`.
3. Find the index of `x`.

---

# 6. Pair

`pair` দিয়ে একসাথে ২টা value রাখা যায়।

Example:

* roll + marks
* x + y
* value + index

---

## 6.1 Basic Pair Example

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    pair<int, int> p;                 // create pair of two integers

    p.first = 10;                     // first value
    p.second = 20;                    // second value

    cout << p.first << " " << p.second << "\n";

    return 0;
}
```

---

## 6.2 Pair Input Example

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    pair<int, int> p;                 // create pair

    cin >> p.first >> p.second;       // input first and second value

    cout << p.first << " " << p.second << "\n";

    return 0;
}
```

---

## 6.3 Vector of Pair

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<pair<int, int>> v;         // vector of pairs

    v.push_back({1, 100});            // add first pair
    v.push_back({2, 200});            // add second pair
    v.push_back({3, 300});            // add third pair

    for (int i = 0; i < v.size(); i++) {
        cout << v[i].first << " " << v[i].second << "\n";
    }

    return 0;
}
```

---

## 6.4 Pair Practice

1. Input two integers in a pair.
2. Store 3 pairs in a vector.
3. Print all first values.
4. Print all second values.

---

# 7. Stack

Stack follows **LIFO**
মানে: **Last In, First Out**

যেটা সবার শেষে ঢুকবে, সেটা সবার আগে বের হবে।

উদাহরণ:

* বইয়ের stack
* plates stack

---

## 7.1 Stack Operations

* `push(x)` → নতুন element যোগ করে
* `pop()` → top element remove করে
* `top()` → top element দেখায়
* `empty()` → stack empty কি না check করে

---

## 7.2 Stack Full Demo Code

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    stack<int> st;                        // create empty stack

    st.push(10);                          // push 10
    st.push(20);                          // push 20
    st.push(30);                          // push 30

    cout << st.top() << "\n";            // print top element

    st.pop();                             // remove top element

    cout << st.top() << "\n";            // print new top element

    if (st.empty()) {                     // check if empty
        cout << "Stack is empty\n";
    } else {
        cout << "Stack is not empty\n";
    }

    st.pop();                             // remove top
    st.pop();                             // remove top

    if (st.empty()) {                     // check again
        cout << "Now stack is empty\n";
    } else {
        cout << "Now stack is not empty\n";
    }

    return 0;
}
```

---

## 7.3 Stack Practice

1. Push three numbers.
2. Print top element.
3. Pop one element.
4. Print top again.
5. Check if the stack is empty.

---

# 8. Queue

Queue follows **FIFO**
মানে: **First In, First Out**

যেটা সবার আগে ঢুকবে, সেটা সবার আগে বের হবে।

উদাহরণ:

* লাইনে দাঁড়ানো মানুষ
* token line
* bus queue

---

## 8.1 Queue Operations

* `push(x)` → element add করে
* `pop()` → সামনে থাকা element remove করে
* `front()` → সামনে থাকা element দেখায়
* `back()` → শেষের element দেখায়
* `empty()` → queue empty কি না check করে

---

## 8.2 Queue Full Demo Code

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    queue<int> q;                         // create empty queue

    q.push(10);                           // add 10
    q.push(20);                           // add 20
    q.push(30);                           // add 30

    cout << q.front() << "\n";           // print front element
    cout << q.back() << "\n";            // print last element

    q.pop();                              // remove front element

    cout << q.front() << "\n";           // print new front element

    if (q.empty()) {                      // check if queue is empty
        cout << "Queue is empty\n";
    } else {
        cout << "Queue is not empty\n";
    }

    q.pop();                              // remove front
    q.pop();                              // remove front

    if (q.empty()) {                      // check again
        cout << "Now queue is empty\n";
    } else {
        cout << "Now queue is not empty\n";
    }

    return 0;
}
```

---

## 8.3 Stack vs Queue

### Stack

* LIFO
* last inserted বের হয় আগে

### Queue

* FIFO
* first inserted বের হয় আগে

---

## 8.4 Queue Practice

1. Push three values.
2. Print front value.
3. Print back value.
4. Pop one value.
5. Print new front value.
6. Check whether queue is empty.

---

# 9. Short Summary Note

আজকে যা শিখেছি:

* **Time Complexity** দিয়ে বোঝা যায় program কত efficient
* **Vector** হলো dynamic array
* **Sort** data-কে order-এ সাজায়
* **Binary Search** sorted data-তে fast search করে
* **Pair** দিয়ে দুইটা value একসাথে রাখা যায়
* **Stack** হলো LIFO structure
* **Queue** হলো FIFO structure

---

# 10. Quick Quiz

## 10.1 Concept Questions

1. `O(n)` আর `O(log n)` এর মধ্যে কোনটা faster?
2. Vector আর array-এর main difference কী?
3. Binary search use করতে হলে কী লাগবে?
4. Sort-এর complexity কী?
5. `pair<int,int>`-এ value access করতে কী use করি?
6. Stack-এর rule কী?
7. Queue-এর rule কী?
8. `st.top()` কী করে?
9. `q.front()` কী করে?
10. `q.back()` কী করে?

---

## 10.2 Code Questions

1. `vector<int> v;` কী করে?
2. `v.push_back(5);` কী করে?
3. `v.pop_back();` কী করে?
4. `sort(v.begin(), v.end());` কী করে?
5. `p.first` মানে কী?
6. `st.push(10);` কী করে?
7. `st.pop();` কী করে?
8. `q.push(7);` কী করে?
9. `q.pop();` কী করে?
10. Binary search কেন sorted data-তে use করা হয়?

---

# 11. Suggested Mini Practice Set

## Vector

* Input `n`, print all values
* Find sum
* Count odd numbers
* Find maximum

## Sort

* Sort and print
* Print largest and smallest
* Descending sort

## Binary Search

* Search for `x`
* Print `YES/NO`
* Print found/not found

## Pair

* Take 2 integers as a pair
* Store 3 pairs in a vector and print them

## Stack

* Push 3 values
* Print top
* Pop 1
* Print top again

## Queue

* Push 3 values
* Print front and back
* Pop 1
* Print front again

---

# 12. Final Connection Between Topics

আজকের class-এর main connection হলো:

* array → vector
* unsorted → sort
* linear search → binary search
* one value + another value → pair
* last in first out → stack
* first in first out → queue

যদি এই connection clear থাকে, তাহলে পরে `set`, `map`, `priority_queue` এবং আরও STL topic শেখা অনেক easy হয়ে যাবে।

---

# 13. Final Reminder

আজকের class শেষে student যেন এই জিনিসগুলো confidently বলতে পারে:

* vector কী
* sort কীভাবে use করতে হয়
* binary search কখন use করা যায়
* pair কী কাজে লাগে
* stack কীভাবে কাজ করে
* queue কীভাবে কাজ করে
