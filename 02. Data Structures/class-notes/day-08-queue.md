# Queue — Teaching Plan & Competitive Programming Notes

**Course context:** ICT 2101 Data Structures — Queue: introduction, queue implementation using array and linked list, queue operations, and circular queue.  
**CP focus:** problem-solving patterns where First-In-First-Out (FIFO) behavior gives an efficient solution.

---

## 1. Learning Outcomes

After this module, students should be able to:

1. Explain Queue as an Abstract Data Type (ADT).
2. Identify FIFO behavior in real-life and programming problems.
3. Implement Queue using:
   - Array
   - Circular array
   - Linked list
   - STL `queue`
   - STL `deque`
4. Analyze time and space complexity of queue operations.
5. Apply queue in competitive programming problems:
   - BFS in graph/grid
   - Level order traversal
   - Shortest path in unweighted graph
   - Sliding window using deque
   - Circular queue simulation
   - Multi-source BFS
   - Topological sort

---

## 2. Prerequisites

Students should already know:

- Basic C/C++ syntax
- Array and pointer basics
- Linked list basics
- Graph basics for BFS
- Basic complexity analysis
- Stack vs queue conceptual difference

---

## 3. Core Concept: What is a Queue?

A **Queue** is a linear data structure where insertion happens at the rear/back and deletion happens from the front.

### Rule

> First In, First Out — **FIFO**

The first element inserted is the first element removed.

### Real-life examples

- Line at bank counter
- Printer job queue
- CPU process scheduling
- Call center waiting line
- BFS traversal

---

## 4. Queue ADT Operations

| Operation | Meaning | Complexity |
|---|---|---|
| `push(x)` / `enqueue(x)` | Insert at rear | `O(1)` |
| `pop()` / `dequeue()` | Remove from front | `O(1)` |
| `front()` | Access front element | `O(1)` |
| `back()` | Access rear element | `O(1)` |
| `empty()` | Check empty | `O(1)` |
| `size()` | Number of elements | `O(1)` if maintained |

### Important edge cases

- Pop from empty queue → underflow
- Front from empty queue → invalid access
- Push into full fixed-size queue → overflow
- In simple array queue, unused space may appear at the front after pops

---

## 5. Simple Queue Implementation Using Array

### Idea

Maintain two pointers:

- `frontIndex`
- `rearIndex`

```cpp
#include <bits/stdc++.h>
using namespace std;

class QueueArray {
private:
    int arr[1000];
    int frontIndex;
    int rearIndex;

public:
    QueueArray() {
        frontIndex = 0;
        rearIndex = -1;
    }

    bool empty() {
        return frontIndex > rearIndex;
    }

    bool full() {
        return rearIndex == 999;
    }

    void push(int x) {
        if (full()) {
            cout << "Queue Overflow\n";
            return;
        }
        arr[++rearIndex] = x;
    }

    void pop() {
        if (empty()) {
            cout << "Queue Underflow\n";
            return;
        }
        frontIndex++;
    }

    int front() {
        if (empty()) {
            cout << "Queue is empty\n";
            return -1;
        }
        return arr[frontIndex];
    }

    int size() {
        return rearIndex - frontIndex + 1;
    }
};

int main() {
    QueueArray q;

    q.push(10);
    q.push(20);
    q.push(30);

    cout << q.front() << "\n"; // 10

    q.pop();

    cout << q.front() << "\n"; // 20
}
```

### Limitation

After many pops, the front part of the array becomes unused.  
This is why circular queue is important.

---

## 6. Circular Queue

A **Circular Queue** treats the array as circular.  
When the rear reaches the end, it can wrap around to the beginning if there is empty space.

### Formula

```cpp
nextIndex = (currentIndex + 1) % capacity;
```

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

class CircularQueue {
private:
    vector<int> arr;
    int frontIndex;
    int rearIndex;
    int currentSize;
    int capacity;

public:
    CircularQueue(int cap) {
        capacity = cap;
        arr.resize(capacity);
        frontIndex = 0;
        rearIndex = -1;
        currentSize = 0;
    }

    bool empty() {
        return currentSize == 0;
    }

    bool full() {
        return currentSize == capacity;
    }

    void push(int x) {
        if (full()) {
            cout << "Queue Overflow\n";
            return;
        }

        rearIndex = (rearIndex + 1) % capacity;
        arr[rearIndex] = x;
        currentSize++;
    }

    void pop() {
        if (empty()) {
            cout << "Queue Underflow\n";
            return;
        }

        frontIndex = (frontIndex + 1) % capacity;
        currentSize--;
    }

    int front() {
        if (empty()) {
            cout << "Queue is empty\n";
            return -1;
        }

        return arr[frontIndex];
    }

    int size() {
        return currentSize;
    }
};

int main() {
    CircularQueue q(5);

    q.push(10);
    q.push(20);
    q.push(30);
    q.pop();
    q.push(40);
    q.push(50);
    q.push(60);

    cout << q.front() << "\n";
}
```

---

## 7. Queue Implementation Using Linked List

### Idea

Maintain:

- `frontNode`
- `rearNode`

Insert at rear, delete from front.

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

class QueueLinkedList {
private:
    Node* frontNode;
    Node* rearNode;

public:
    QueueLinkedList() {
        frontNode = nullptr;
        rearNode = nullptr;
    }

    bool empty() {
        return frontNode == nullptr;
    }

    void push(int x) {
        Node* newNode = new Node(x);

        if (empty()) {
            frontNode = rearNode = newNode;
        } else {
            rearNode->next = newNode;
            rearNode = newNode;
        }
    }

    void pop() {
        if (empty()) {
            cout << "Queue Underflow\n";
            return;
        }

        Node* temp = frontNode;
        frontNode = frontNode->next;

        if (frontNode == nullptr) {
            rearNode = nullptr;
        }

        delete temp;
    }

    int front() {
        if (empty()) {
            cout << "Queue is empty\n";
            return -1;
        }

        return frontNode->data;
    }
};
```

---

## 8. Queue Using STL

For competitive programming, use STL queue most of the time.

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    queue<int> q;

    q.push(10);
    q.push(20);

    cout << q.front() << "\n"; // 10
    cout << q.back() << "\n";  // 20

    q.pop();

    cout << q.front() << "\n"; // 20
}
```

### STL Queue common functions

| Function | Use |
|---|---|
| `q.push(x)` | Insert at back |
| `q.pop()` | Remove front, does not return value |
| `q.front()` | Access front |
| `q.back()` | Access back |
| `q.empty()` | Check empty |
| `q.size()` | Size |

### Common CP warning

`pop()` does not return the front element.  
Use:

```cpp
int x = q.front();
q.pop();
```

---

## 9. Deque: Double-Ended Queue

A `deque` allows insertion and deletion at both ends.

```cpp
deque<int> dq;

dq.push_back(10);
dq.push_front(5);

cout << dq.front() << "\n"; // 5
cout << dq.back() << "\n";  // 10

dq.pop_front();
dq.pop_back();
```

### Why `deque` matters in CP

Use `deque` for:

- Sliding window maximum/minimum
- 0-1 BFS
- Palindrome simulation
- Maintaining candidates from both sides

---

## 10. Application 1: BFS in Graph

### Problem

Traverse graph level by level from a source node.

### Why queue?

BFS processes nodes in the order they are discovered.  
That is exactly FIFO.

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
    queue<int> q;

    q.push(1);
    visited[1] = true;

    while (!q.empty()) {
        int node = q.front();
        q.pop();

        cout << node << " ";

        for (int child : graph[node]) {
            if (!visited[child]) {
                visited[child] = true;
                q.push(child);
            }
        }
    }
}
```

### Complexity

- Time: `O(n + m)`
- Space: `O(n)`

---

## 11. Application 2: Shortest Path in Unweighted Graph

BFS can find shortest path when every edge has equal weight.

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n, m, source;
    cin >> n >> m >> source;

    vector<vector<int>> graph(n + 1);

    for (int i = 0; i < m; i++) {
        int u, v;
        cin >> u >> v;
        graph[u].push_back(v);
        graph[v].push_back(u);
    }

    vector<int> dist(n + 1, -1);
    queue<int> q;

    dist[source] = 0;
    q.push(source);

    while (!q.empty()) {
        int node = q.front();
        q.pop();

        for (int child : graph[node]) {
            if (dist[child] == -1) {
                dist[child] = dist[node] + 1;
                q.push(child);
            }
        }
    }

    for (int i = 1; i <= n; i++) {
        cout << "Distance from " << source << " to " << i << " = " << dist[i] << "\n";
    }
}
```

---

## 12. Application 3: BFS in Grid

Grid BFS is very common in competitive programming.

### Movement arrays

```cpp
int dx[] = {1, -1, 0, 0};
int dy[] = {0, 0, 1, -1};
```

### Code

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n, m;
    cin >> n >> m;

    vector<string> grid(n);
    for (int i = 0; i < n; i++) cin >> grid[i];

    int sx, sy;
    cin >> sx >> sy;

    vector<vector<int>> dist(n, vector<int>(m, -1));
    queue<pair<int, int>> q;

    dist[sx][sy] = 0;
    q.push({sx, sy});

    int dx[] = {1, -1, 0, 0};
    int dy[] = {0, 0, 1, -1};

    while (!q.empty()) {
        auto [x, y] = q.front();
        q.pop();

        for (int dir = 0; dir < 4; dir++) {
            int nx = x + dx[dir];
            int ny = y + dy[dir];

            if (nx < 0 || nx >= n || ny < 0 || ny >= m) continue;
            if (grid[nx][ny] == '#') continue;
            if (dist[nx][ny] != -1) continue;

            dist[nx][ny] = dist[x][y] + 1;
            q.push({nx, ny});
        }
    }
}
```

### CP Problems

- CSES: Labyrinth
- Codeforces grid BFS problems
- UVA: Knight Moves
- LightOJ grid shortest path problems

---

## 13. Application 4: Multi-source BFS

### Idea

Start BFS from multiple sources at once.

Useful for:

- Fire spread problems
- Nearest hospital/source
- Rotten oranges
- Monster escape problems

```cpp
queue<pair<int, int>> q;

for (int i = 0; i < n; i++) {
    for (int j = 0; j < m; j++) {
        if (grid[i][j] == 'F') {
            dist[i][j] = 0;
            q.push({i, j});
        }
    }
}
```

All sources enter the queue initially with distance `0`.

---

## 14. Application 5: Sliding Window Maximum Using Deque

### Problem

Given array and window size `k`, find maximum of every window.

### Naive solution

Each window scan → `O(nk)`

### Deque solution

Maintain indices in decreasing order of values.

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n, k;
    cin >> n >> k;

    vector<int> a(n);
    for (int i = 0; i < n; i++) cin >> a[i];

    deque<int> dq;

    for (int i = 0; i < n; i++) {
        while (!dq.empty() && dq.front() <= i - k) {
            dq.pop_front();
        }

        while (!dq.empty() && a[dq.back()] <= a[i]) {
            dq.pop_back();
        }

        dq.push_back(i);

        if (i >= k - 1) {
            cout << a[dq.front()] << " ";
        }
    }

    cout << "\n";
}
```

### Complexity

- Time: `O(n)`
- Space: `O(k)`

---

## 15. Application 6: Topological Sort Using Queue

For Directed Acyclic Graph (DAG), Kahn's algorithm uses queue.

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n, m;
    cin >> n >> m;

    vector<vector<int>> graph(n + 1);
    vector<int> indegree(n + 1, 0);

    for (int i = 0; i < m; i++) {
        int u, v;
        cin >> u >> v;
        graph[u].push_back(v);
        indegree[v]++;
    }

    queue<int> q;

    for (int i = 1; i <= n; i++) {
        if (indegree[i] == 0) q.push(i);
    }

    vector<int> order;

    while (!q.empty()) {
        int node = q.front();
        q.pop();

        order.push_back(node);

        for (int child : graph[node]) {
            indegree[child]--;

            if (indegree[child] == 0) {
                q.push(child);
            }
        }
    }

    if ((int)order.size() != n) {
        cout << "Cycle exists\n";
    } else {
        for (int x : order) cout << x << " ";
        cout << "\n";
    }
}
```

---

## 16. Application 7: 0-1 BFS Using Deque

If edge weights are only `0` or `1`, we can use deque instead of Dijkstra.

### Rule

- Weight `0` edge → push front
- Weight `1` edge → push back

```cpp
#include <bits/stdc++.h>
using namespace std;

const int INF = 1e9;

int main() {
    int n, m;
    cin >> n >> m;

    vector<vector<pair<int, int>>> graph(n + 1);

    for (int i = 0; i < m; i++) {
        int u, v, w;
        cin >> u >> v >> w; // w should be 0 or 1
        graph[u].push_back({v, w});
        graph[v].push_back({u, w});
    }

    vector<int> dist(n + 1, INF);
    deque<int> dq;

    dist[1] = 0;
    dq.push_front(1);

    while (!dq.empty()) {
        int node = dq.front();
        dq.pop_front();

        for (auto [child, weight] : graph[node]) {
            if (dist[node] + weight < dist[child]) {
                dist[child] = dist[node] + weight;

                if (weight == 0) dq.push_front(child);
                else dq.push_back(child);
            }
        }
    }

    cout << dist[n] << "\n";
}
```

---

## 17. Teaching Flow

### Class 1: Concept + Basic Queue

1. Explain FIFO using real-life examples.
2. Demonstrate enqueue, dequeue, front, rear.
3. Implement queue using simple array.
4. Discuss limitation of simple array queue.

### Class 2: Circular Queue + Linked List

1. Explain circular array using diagram.
2. Implement circular queue.
3. Implement linked-list queue.
4. Compare memory and performance.

### Class 3: STL Queue + BFS

1. Introduce STL `queue`.
2. Solve graph BFS.
3. Solve shortest path in unweighted graph.
4. Solve grid BFS.

### Class 4: CP Advanced Queue Patterns

1. Multi-source BFS.
2. `deque` and sliding window.
3. Topological sort.
4. 0-1 BFS.

---

## 18. Classroom Demonstration

Given operations:

```text
push(10)
push(20)
push(30)
pop()
push(40)
front()
```

Final queue:

```text
Front -> 20 30 40 <- Rear
```

Output of `front()` is `20`.

---

## 19. Stack vs Queue

| Feature | Stack | Queue |
|---|---|---|
| Order | LIFO | FIFO |
| Insert | Top | Rear |
| Delete | Top | Front |
| CP use | Brackets, monotonic stack, DFS | BFS, shortest path, scheduling |
| STL | `stack` | `queue` |

---

## 20. Common Mistakes

1. Calling `front()` when queue is empty.
2. Thinking `pop()` returns value.
3. Confusing `front()` and `back()`.
4. Using stack for BFS.
5. Forgetting to mark visited before pushing into queue.
6. In grid BFS, not checking boundary.
7. In sliding window, storing values instead of indices.
8. In circular queue, wrong modulo formula.

---

## 21. CP Pattern Recognition

Use queue when:

- Processing should happen in arrival order.
- You need level-by-level traversal.
- You need shortest path in unweighted graph.
- A simulation requires waiting line behavior.
- Multiple sources spread at the same time.
- You need to process nodes with indegree `0`.
- You need sliding window candidates using `deque`.

---

## 22. Practice Problems

### Beginner

1. Implement queue using array.
2. Implement circular queue.
3. Implement queue using linked list.
4. Reverse first `k` elements of a queue.
5. Generate binary numbers from `1` to `n` using queue.

### Intermediate

1. BFS traversal of graph.
2. Shortest path in unweighted graph.
3. Grid shortest path.
4. Rotten oranges / spreading problem.
5. Number of islands using BFS.
6. Topological sort using Kahn's algorithm.

### Advanced

1. CSES Labyrinth
2. CSES Monsters
3. Sliding Window Maximum
4. 0-1 BFS
5. Minimum moves in grid with obstacles
6. Knight shortest path
7. Word ladder style BFS

### Suggested online platforms

- Codeforces
- CSES
- LeetCode
- HackerRank
- AtCoder
- LightOJ
- UVA Online Judge

---

## 23. Mini Contest Plan

Duration: 120 minutes

| Problem | Topic | Difficulty |
|---|---|---|
| A | Queue implementation | Easy |
| B | Circular queue simulation | Easy |
| C | Graph BFS | Medium |
| D | Grid BFS | Medium |
| E | Sliding window maximum | Medium-Hard |
| F | 0-1 BFS | Hard |

---

## 24. Assignment

1. Implement queue using array, circular array, and linked list.
2. Compare simple queue and circular queue.
3. Solve at least 5 BFS/queue CP problems.
4. Write complexity analysis for each solution.
5. Explain why BFS gives shortest path in an unweighted graph.

---

## 25. Quick Revision Sheet

- Queue follows FIFO.
- `push`, `pop`, `front`, `back` are `O(1)`.
- Circular queue solves wasted-space issue of simple array queue.
- STL `queue` is enough for normal FIFO problems.
- Use `deque` when both front and back operations are needed.
- BFS is the most important queue application in CP.
- Always mark visited before pushing to avoid duplicate processing.