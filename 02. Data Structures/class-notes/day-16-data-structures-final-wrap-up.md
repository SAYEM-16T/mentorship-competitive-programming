নিচের notes ta তুমি **teacher-er preparation note** হিসেবে পড়ো। তোমার student-ke সব code মুখস্থ করানো লাগবে না। Last class-er goal হবে: **concept clear + small code দেখানো + future-e nijey revise korte parbe এমন confidence দেওয়া**।

IIT-JU syllabus-er Data Structures Lab অংশেও exactly এই ধরনের practical topics আছে: pointer/linked list, add/delete/find/circular linked list, BST operation, tree traversal, heap, BFS/DFS, MST, Dijkstra, hash table collision resolution etc. তাই তোমার final class এই syllabus-aligned way-te নিলে best হবে।  Data Structures course/lab second year first semester-e থাকে, তাই এখন basic foundation দেওয়া future university preparation-er জন্য useful. 

আমি C++ দিয়ে code দিচ্ছি, কারণ CP/university DSA শেখানোর জন্য সবচেয়ে practical। Student যদি C পড়ে, concept same থাকবে, শুধু syntax একটু বদলাবে।

---

# Overall Teaching Flow

তাকে শুরুতেই বলবা:

> “Aajke amra shob kichu deep theory hisebe na, ekta mental map hisebe shikhbo. Tumi jeno bujhte paro kon data structure keno use hoy, kivabe kaj kore, and code-er basic structure kemon.”

Full roadmap:

```text
Array
  ↓
Linked List
  ↓
Tree / BST
  ↓
Traversal
  ↓
Heap
  ↓
Graph
  ↓
Hashing
```

একটা common line বারবার use করবা:

> Data Structure mane data rakhar smart system. Algorithm mane oi data-r upor kaj korar process.

---

# Day 05: Linked List Basics

## 1. Linked List কী?

Array-te data continuous memory-te থাকে।

```text
Array:
[10][20][30][40]
```

Linked List-e data আলাদা আলাদা node-e থাকে, আর প্রতিটা node next node-er address রাখে।

```text
Linked List:
[10 | next] -> [20 | next] -> [30 | next] -> NULL
```

প্রতিটা node-এর 2 part:

```text
data  = actual value
next  = next node-er address
```

তোমার student-ke বলবা:

> “Linked list holo train-er moto. Prottek coach-e data ache, ar next coach-er connection ache.”

## 2. Node কী?

C++-এ node structure:

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;

    Node(int value) {
        data = value;
        next = nullptr;
    }
};
```

Explain:

```cpp
int data;
```

মানে node-er ভিতরে value থাকবে।

```cpp
Node* next;
```

মানে next আরেকটা Node-er address রাখবে।

```cpp
nullptr
```

মানে এখন কোনো next node নাই।

---

## 3. Head কী?

Linked list-er প্রথম node-ke point kore `head`.

```text
head
 ↓
[10 | next] -> [20 | next] -> [30 | NULL]
```

যদি list empty হয়:

```cpp
Node* head = nullptr;
```

Explain:

> “Head holo linked list-er entry point. Head হারিয়ে গেলে পুরো list access করা যাবে না।”

---

## 4. Traversal কী?

Traversal মানে start থেকে end পর্যন্ত ঘুরে ঘুরে node দেখা।

```cpp
void printList(Node* head) {
    Node* current = head;

    while (current != nullptr) {
        cout << current->data << " ";
        current = current->next;
    }

    cout << endl;
}
```

Explain:

```cpp
Node* current = head;
```

আমরা head থেকে শুরু করছি।

```cpp
while (current != nullptr)
```

যতক্ষণ node আছে, ততক্ষণ চলবে।

```cpp
current = current->next;
```

next node-e move করছি।

Student-ke visual দাও:

```text
current
   ↓
[10] -> [20] -> [30] -> NULL

After one step:

        current
          ↓
[10] -> [20] -> [30] -> NULL
```

---

## 5. Complete Basic Linked List Code

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;

    Node(int value) {
        data = value;
        next = nullptr;
    }
};

void printList(Node* head) {
    Node* current = head;

    while (current != nullptr) {
        cout << current->data << " ";
        current = current->next;
    }

    cout << endl;
}

int main() {
    Node* head = new Node(10);
    head->next = new Node(20);
    head->next->next = new Node(30);

    printList(head);

    return 0;
}
```

Output:

```text
10 20 30
```

## Student-ke ask korba

“Head কোন node-ke point করছে?”
“30-er next কেন NULL?”
“current = current->next না দিলে কী হবে?”

Correct answer:

* Head first node point করে।
* 30 last node, তাই next নেই।
* Infinite loop হতে পারে।

---

# Day 06: Linked List Operations

এই topic-e তুমি বলবা:

> “Linked list-e main kaj holo add, delete, search, print.”

---

## 1. Insert at Beginning

আগে নতুন node বানাবো। তারপর new node-er next হবে old head। তারপর head হবে new node।

Before:

```text
head
 ↓
[20] -> [30] -> NULL
```

Insert 10:

```text
[10] -> [20] -> [30] -> NULL
 ↑
head
```

Code:

```cpp
void insertAtBeginning(Node*& head, int value) {
    Node* newNode = new Node(value);
    newNode->next = head;
    head = newNode;
}
```

Important: `Node*& head`

Explain:

> “Head change korte hobe, tai reference diye pathacchi.”

---

## 2. Insert at End

End-e যেতে হবে, তারপর last node-er next নতুন node হবে।

```cpp
void insertAtEnd(Node*& head, int value) {
    Node* newNode = new Node(value);

    if (head == nullptr) {
        head = newNode;
        return;
    }

    Node* current = head;

    while (current->next != nullptr) {
        current = current->next;
    }

    current->next = newNode;
}
```

Explain:

```cpp
while (current->next != nullptr)
```

এখানে আমরা last node খুঁজছি। Last node-er next NULL.

---

## 3. Search in Linked List

```cpp
bool search(Node* head, int target) {
    Node* current = head;

    while (current != nullptr) {
        if (current->data == target) {
            return true;
        }

        current = current->next;
    }

    return false;
}
```

Example:

```text
10 -> 20 -> 30 -> NULL

Search 20 = found
Search 50 = not found
```

Time complexity: `O(n)`
কারণ worst case-e সব node check করতে হতে পারে।

---

## 4. Delete by Value

Case 1: List empty
Case 2: Delete head
Case 3: Delete middle/end node

```cpp
void deleteValue(Node*& head, int value) {
    if (head == nullptr) {
        return;
    }

    if (head->data == value) {
        Node* temp = head;
        head = head->next;
        delete temp;
        return;
    }

    Node* current = head;

    while (current->next != nullptr && current->next->data != value) {
        current = current->next;
    }

    if (current->next != nullptr) {
        Node* temp = current->next;
        current->next = current->next->next;
        delete temp;
    }
}
```

Visual:

Delete 20:

```text
Before:
10 -> 20 -> 30 -> NULL

After:
10 -> 30 -> NULL
```

Main logic:

```cpp
current->next = current->next->next;
```

মানে 20 কে skip করে 10 সরাসরি 30-এর সাথে connect.

---

## 5. Reverse Linked List

এটা একটু advanced, কিন্তু last class-e concept দিলে ভালো।

Before:

```text
10 -> 20 -> 30 -> NULL
```

After:

```text
30 -> 20 -> 10 -> NULL
```

Code:

```cpp
void reverseList(Node*& head) {
    Node* prev = nullptr;
    Node* current = head;
    Node* nextNode = nullptr;

    while (current != nullptr) {
        nextNode = current->next;
        current->next = prev;
        prev = current;
        current = nextNode;
    }

    head = prev;
}
```

তাকে dry run করাও:

```text
prev = NULL
current = 10
nextNode = 20

10-er next NULL kore dilam
then prev = 10
current = 20
```

---

## 6. Full Linked List Operations Code

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;

    Node(int value) {
        data = value;
        next = nullptr;
    }
};

void insertAtBeginning(Node*& head, int value) {
    Node* newNode = new Node(value);
    newNode->next = head;
    head = newNode;
}

void insertAtEnd(Node*& head, int value) {
    Node* newNode = new Node(value);

    if (head == nullptr) {
        head = newNode;
        return;
    }

    Node* current = head;

    while (current->next != nullptr) {
        current = current->next;
    }

    current->next = newNode;
}

bool search(Node* head, int target) {
    Node* current = head;

    while (current != nullptr) {
        if (current->data == target) {
            return true;
        }

        current = current->next;
    }

    return false;
}

void deleteValue(Node*& head, int value) {
    if (head == nullptr) {
        return;
    }

    if (head->data == value) {
        Node* temp = head;
        head = head->next;
        delete temp;
        return;
    }

    Node* current = head;

    while (current->next != nullptr && current->next->data != value) {
        current = current->next;
    }

    if (current->next != nullptr) {
        Node* temp = current->next;
        current->next = current->next->next;
        delete temp;
    }
}

void printList(Node* head) {
    Node* current = head;

    while (current != nullptr) {
        cout << current->data << " ";
        current = current->next;
    }

    cout << endl;
}

int main() {
    Node* head = nullptr;

    insertAtEnd(head, 10);
    insertAtEnd(head, 20);
    insertAtEnd(head, 30);
    insertAtBeginning(head, 5);

    printList(head);

    cout << search(head, 20) << endl;

    deleteValue(head, 20);
    printList(head);

    return 0;
}
```

Output:

```text
5 10 20 30
1
5 10 30
```

---

# Day 09: Tree and BST

## 1. Tree কী?

Tree হলো hierarchical data structure.

Real-life example:

```text
University
 ├── Faculty
 │    ├── Department
 │    └── Institute
 └── Administration
```

Computer example:

```text
Folder
 ├── file1
 ├── file2
 └── subfolder
```

Tree terms:

```text
Root      = top node
Child     = নিচের node
Parent    = উপরের node
Leaf      = যার কোনো child নাই
Edge      = connection
Height    = longest path from root to leaf
```

Example:

```text
        10
       /  \
      5    20
     / \     \
    3   7     30
```

Root = 10
Leaf = 3, 7, 30
Parent of 5 = 10
Children of 5 = 3, 7

---

## 2. Binary Tree কী?

যে tree-তে প্রতিটা node-এর maximum 2 child থাকে।

```text
left child
right child
```

C++ node:

```cpp
struct TreeNode {
    int data;
    TreeNode* left;
    TreeNode* right;

    TreeNode(int value) {
        data = value;
        left = nullptr;
        right = nullptr;
    }
};
```

---

## 3. BST কী?

BST = Binary Search Tree.

Rule:

```text
Left subtree-er shob value root-er cheye small
Right subtree-er shob value root-er cheye large
```

Example:

```text
        50
       /  \
     30    70
    / \    / \
   20 40  60 80
```

Explain:

* 30 < 50 তাই left
* 70 > 50 তাই right
* 20 < 30 তাই 30-er left
* 40 > 30 তাই 30-er right

---

## 4. BST Insert

Logic:

```text
new value < root → left side
new value > root → right side
```

Code:

```cpp
TreeNode* insertBST(TreeNode* root, int value) {
    if (root == nullptr) {
        return new TreeNode(value);
    }

    if (value < root->data) {
        root->left = insertBST(root->left, value);
    } else if (value > root->data) {
        root->right = insertBST(root->right, value);
    }

    return root;
}
```

Explain:

> “Root null mane ekhane node boshano jabe.”

---

## 5. BST Search

```cpp
bool searchBST(TreeNode* root, int target) {
    if (root == nullptr) {
        return false;
    }

    if (root->data == target) {
        return true;
    }

    if (target < root->data) {
        return searchBST(root->left, target);
    }

    return searchBST(root->right, target);
}
```

Example search 60:

```text
50 → 60 greater, go right
70 → 60 smaller, go left
60 → found
```

Time complexity:

Balanced BST: `O(log n)`
Skewed BST: `O(n)`

Explain:

> “BST balanced hole search fast. Kintu one side-e jodi shob node chole jay, eta linked list-er moto slow hoye jay.”

---

## 6. Find Minimum and Maximum in BST

Minimum সবসময় leftmost node.

```cpp
int findMin(TreeNode* root) {
    while (root->left != nullptr) {
        root = root->left;
    }

    return root->data;
}
```

Maximum সবসময় rightmost node.

```cpp
int findMax(TreeNode* root) {
    while (root->right != nullptr) {
        root = root->right;
    }

    return root->data;
}
```

---

## 7. BST Delete

Delete-এর 3 case:

Case 1: Leaf node
Case 2: One child
Case 3: Two children

```cpp
TreeNode* deleteBST(TreeNode* root, int value) {
    if (root == nullptr) {
        return nullptr;
    }

    if (value < root->data) {
        root->left = deleteBST(root->left, value);
    } else if (value > root->data) {
        root->right = deleteBST(root->right, value);
    } else {
        // Case 1 and 2: no child or one child
        if (root->left == nullptr) {
            TreeNode* temp = root->right;
            delete root;
            return temp;
        } else if (root->right == nullptr) {
            TreeNode* temp = root->left;
            delete root;
            return temp;
        }

        // Case 3: two children
        TreeNode* successor = root->right;

        while (successor->left != nullptr) {
            successor = successor->left;
        }

        root->data = successor->data;
        root->right = deleteBST(root->right, successor->data);
    }

    return root;
}
```

Student-ke initially delete deep না করালেও চলবে। শুধু 3 case বুঝাও।

---

# Day 10: Tree Traversal and Heap

## 1. Tree Traversal কী?

Traversal মানে tree-er সব node visit করা।

Three DFS traversal:

```text
Preorder  = Root → Left → Right
Inorder   = Left → Root → Right
Postorder = Left → Right → Root
```

Example tree:

```text
        50
       /  \
     30    70
    / \    / \
   20 40  60 80
```

---

## 2. Preorder

Root আগে।

```text
50 30 20 40 70 60 80
```

Code:

```cpp
void preorder(TreeNode* root) {
    if (root == nullptr) return;

    cout << root->data << " ";
    preorder(root->left);
    preorder(root->right);
}
```

Use case:

* Tree copy করা
* Prefix expression

---

## 3. Inorder

Left আগে, তারপর Root, তারপর Right.

```text
20 30 40 50 60 70 80
```

Important:

> “BST-er inorder traversal always sorted output dey.”

Code:

```cpp
void inorder(TreeNode* root) {
    if (root == nullptr) return;

    inorder(root->left);
    cout << root->data << " ";
    inorder(root->right);
}
```

---

## 4. Postorder

Children আগে, root শেষে।

```text
20 40 30 60 80 70 50
```

Code:

```cpp
void postorder(TreeNode* root) {
    if (root == nullptr) return;

    postorder(root->left);
    postorder(root->right);
    cout << root->data << " ";
}
```

Use case:

* Tree delete করা
* Expression evaluation

---

## 5. Level Order Traversal

Level by level print.

```text
50
30 70
20 40 60 80
```

Code:

```cpp
#include <queue>

void levelOrder(TreeNode* root) {
    if (root == nullptr) return;

    queue<TreeNode*> q;
    q.push(root);

    while (!q.empty()) {
        TreeNode* current = q.front();
        q.pop();

        cout << current->data << " ";

        if (current->left != nullptr) {
            q.push(current->left);
        }

        if (current->right != nullptr) {
            q.push(current->right);
        }
    }
}
```

Explain:

> “Queue use kore amra age jeta ashche seta age process kori. Tai level by level jai.”

---

## 6. Full BST + Traversal Code

```cpp
#include <iostream>
#include <queue>
using namespace std;

struct TreeNode {
    int data;
    TreeNode* left;
    TreeNode* right;

    TreeNode(int value) {
        data = value;
        left = nullptr;
        right = nullptr;
    }
};

TreeNode* insertBST(TreeNode* root, int value) {
    if (root == nullptr) {
        return new TreeNode(value);
    }

    if (value < root->data) {
        root->left = insertBST(root->left, value);
    } else if (value > root->data) {
        root->right = insertBST(root->right, value);
    }

    return root;
}

void inorder(TreeNode* root) {
    if (root == nullptr) return;

    inorder(root->left);
    cout << root->data << " ";
    inorder(root->right);
}

void preorder(TreeNode* root) {
    if (root == nullptr) return;

    cout << root->data << " ";
    preorder(root->left);
    preorder(root->right);
}

void postorder(TreeNode* root) {
    if (root == nullptr) return;

    postorder(root->left);
    postorder(root->right);
    cout << root->data << " ";
}

void levelOrder(TreeNode* root) {
    if (root == nullptr) return;

    queue<TreeNode*> q;
    q.push(root);

    while (!q.empty()) {
        TreeNode* current = q.front();
        q.pop();

        cout << current->data << " ";

        if (current->left != nullptr) q.push(current->left);
        if (current->right != nullptr) q.push(current->right);
    }
}

int main() {
    TreeNode* root = nullptr;

    int values[] = {50, 30, 70, 20, 40, 60, 80};

    for (int value : values) {
        root = insertBST(root, value);
    }

    cout << "Inorder: ";
    inorder(root);
    cout << endl;

    cout << "Preorder: ";
    preorder(root);
    cout << endl;

    cout << "Postorder: ";
    postorder(root);
    cout << endl;

    cout << "Level order: ";
    levelOrder(root);
    cout << endl;

    return 0;
}
```

---

# Heap

## 1. Heap কী?

Heap হলো special binary tree.

Two types:

```text
Max Heap: parent >= children
Min Heap: parent <= children
```

Max heap example:

```text
        90
       /  \
     50    70
    / \   / \
   20 30 40 60
```

Root always maximum.

Min heap example:

```text
        10
       /  \
     20    30
    / \   / \
   40 50 60 70
```

Root always minimum.

---

## 2. Heap কেন use হয়?

Priority Queue implement করতে।

Real-life example:

Hospital emergency queue:

```text
Normal queue: age ashche age service
Priority queue: jar emergency beshi, she age service
```

CPU scheduling, shortest path, event simulation, top-k problem—সব জায়গায় heap useful.

---

## 3. Heap Array Representation

Heap usually array দিয়ে store করা হয়।

Index formula:

```text
Parent of i = (i - 1) / 2
Left child  = 2 * i + 1
Right child = 2 * i + 2
```

Array:

```text
[90, 50, 70, 20, 30, 40, 60]
```

Tree:

```text
        90
       /  \
     50    70
    / \   / \
   20 30 40 60
```

---

## 4. C++ Priority Queue

Max heap by default:

```cpp
#include <iostream>
#include <queue>
using namespace std;

int main() {
    priority_queue<int> maxHeap;

    maxHeap.push(30);
    maxHeap.push(10);
    maxHeap.push(50);
    maxHeap.push(20);

    cout << maxHeap.top() << endl; // 50

    maxHeap.pop();

    cout << maxHeap.top() << endl; // 30

    return 0;
}
```

Min heap:

```cpp
#include <iostream>
#include <queue>
#include <vector>
using namespace std;

int main() {
    priority_queue<int, vector<int>, greater<int>> minHeap;

    minHeap.push(30);
    minHeap.push(10);
    minHeap.push(50);
    minHeap.push(20);

    cout << minHeap.top() << endl; // 10

    return 0;
}
```

---

## 5. Heap Sort Idea

Heap sort steps:

```text
1. Build max heap
2. Root-e max value thakbe
3. Root last element-er sathe swap
4. Heap size komao
5. Heapify kore abar max root-e ano
```

Student-ke just idea দিলেই enough. Last class-e heap sort fully implement না করলেও সমস্যা নাই।

---

# Day 11: Graphs

## 1. Graph কী?

Graph হলো node আর connection-এর structure.

```text
Node/Vertex = point
Edge        = connection
```

Example:

Facebook friend network:

```text
A -- B
|    |
C -- D
```

Road map:

```text
Dhaka -- Savar -- JU
```

Course prerequisite:

```text
Programming → Data Structure → Algorithm
```

---

## 2. Directed vs Undirected Graph

Undirected:

```text
A -- B
```

A থেকে B যাওয়া যায়, B থেকে A-ও যাওয়া যায়।

Directed:

```text
A → B
```

A থেকে B যাওয়া যায়, কিন্তু B থেকে A necessarily না।

---

## 3. Weighted vs Unweighted Graph

Unweighted:

```text
A -- B
```

Weighted:

```text
A --5-- B
```

Weight distance/cost/time represent করতে পারে।

---

## 4. Graph Representation

### Adjacency Matrix

```text
  A B C
A 0 1 1
B 1 0 1
C 1 1 0
```

Good for dense graph. Memory লাগে `O(n²)`.

### Adjacency List

```text
A: B, C
B: A, C
C: A, B
```

Good for most practical cases. Memory efficient.

C++ adjacency list:

```cpp
vector<int> graph[100];
```

---

## 5. BFS — Breadth First Search

BFS level by level যায়।

Example:

```text
        1
       / \
      2   3
     / \
    4   5
```

BFS from 1:

```text
1 2 3 4 5
```

Real use:

* Shortest path in unweighted graph
* Level finding
* Connected component

Code:

```cpp
#include <iostream>
#include <vector>
#include <queue>
using namespace std;

void bfs(int start, vector<int> graph[], int n) {
    vector<bool> visited(n + 1, false);
    queue<int> q;

    visited[start] = true;
    q.push(start);

    while (!q.empty()) {
        int node = q.front();
        q.pop();

        cout << node << " ";

        for (int neighbor : graph[node]) {
            if (!visited[neighbor]) {
                visited[neighbor] = true;
                q.push(neighbor);
            }
        }
    }
}

int main() {
    int n = 5;
    vector<int> graph[n + 1];

    graph[1].push_back(2);
    graph[1].push_back(3);
    graph[2].push_back(1);
    graph[2].push_back(4);
    graph[2].push_back(5);
    graph[3].push_back(1);
    graph[4].push_back(2);
    graph[5].push_back(2);

    bfs(1, graph, n);

    return 0;
}
```

---

## 6. DFS — Depth First Search

DFS deep-e যায়, তারপর backtrack করে।

Example:

```text
1 → 2 → 4
then back
2 → 5
then back
1 → 3
```

Code:

```cpp
#include <iostream>
#include <vector>
using namespace std;

void dfs(int node, vector<int> graph[], vector<bool>& visited) {
    visited[node] = true;
    cout << node << " ";

    for (int neighbor : graph[node]) {
        if (!visited[neighbor]) {
            dfs(neighbor, graph, visited);
        }
    }
}

int main() {
    int n = 5;
    vector<int> graph[n + 1];

    graph[1].push_back(2);
    graph[1].push_back(3);
    graph[2].push_back(1);
    graph[2].push_back(4);
    graph[2].push_back(5);
    graph[3].push_back(1);
    graph[4].push_back(2);
    graph[5].push_back(2);

    vector<bool> visited(n + 1, false);

    dfs(1, graph, visited);

    return 0;
}
```

---

## 7. BFS vs DFS

| Topic                             | BFS            | DFS             |
| --------------------------------- | -------------- | --------------- |
| Style                             | Level by level | Deep path first |
| Data structure                    | Queue          | Recursion/Stack |
| Shortest path in unweighted graph | Good           | Not guaranteed  |
| Connected component               | Yes            | Yes             |
| Maze/path explore                 | Yes            | Yes             |

তাকে বলবা:

> “BFS holo wave-er moto ছড়িয়ে যায়. DFS holo ekta path dhore deep-e dhuke যায়।”

---

## 8. Dijkstra’s Algorithm

Use case:

> Weighted graph-e shortest path ber korte.

Condition:

> Weight negative হওয়া যাবে না।

Example:

```text
1 --4-- 2
1 --1-- 3
3 --2-- 2
2 --1-- 4
3 --5-- 4
```

Shortest from 1:

```text
1 to 1 = 0
1 to 3 = 1
1 to 2 = 3
1 to 4 = 4
```

Code:

```cpp
#include <iostream>
#include <vector>
#include <queue>
#include <climits>
using namespace std;

void dijkstra(int start, vector<pair<int, int>> graph[], int n) {
    vector<int> dist(n + 1, INT_MAX);

    priority_queue<
        pair<int, int>,
        vector<pair<int, int>>,
        greater<pair<int, int>>
    > pq;

    dist[start] = 0;
    pq.push({0, start});

    while (!pq.empty()) {
        int currentDistance = pq.top().first;
        int node = pq.top().second;
        pq.pop();

        if (currentDistance > dist[node]) {
            continue;
        }

        for (auto edge : graph[node]) {
            int neighbor = edge.first;
            int weight = edge.second;

            if (dist[node] + weight < dist[neighbor]) {
                dist[neighbor] = dist[node] + weight;
                pq.push({dist[neighbor], neighbor});
            }
        }
    }

    for (int i = 1; i <= n; i++) {
        cout << "Distance from " << start << " to " << i << " = " << dist[i] << endl;
    }
}

int main() {
    int n = 4;
    vector<pair<int, int>> graph[n + 1];

    graph[1].push_back({2, 4});
    graph[2].push_back({1, 4});

    graph[1].push_back({3, 1});
    graph[3].push_back({1, 1});

    graph[3].push_back({2, 2});
    graph[2].push_back({3, 2});

    graph[2].push_back({4, 1});
    graph[4].push_back({2, 1});

    graph[3].push_back({4, 5});
    graph[4].push_back({3, 5});

    dijkstra(1, graph, n);

    return 0;
}
```

Explain simply:

> “Dijkstra always currently shortest known node choose kore, then tar neighbor-gulo update kore.”

---

## 9. MST — Minimum Spanning Tree

MST মানে:

> সব node connect করতে হবে, কিন্তু total edge cost minimum হতে হবে।

Example:

```text
Campus-er shob building fiber cable diye connect korte hobe, but cost minimum rakhte hobe.
```

MST algorithms:

```text
Kruskal
Prim
```

Last class-e শুধু concept দাও। Code না দিলেও হবে, কারণ BFS/DFS + Dijkstra already enough heavy.

---

# Day 12: Hashing and Revision

## 1. Hashing কী?

Hashing হলো fast search technique.

Array search:

```text
O(n)
```

Hash table average search:

```text
O(1)
```

Example:

Student ID store করতে চাই।

```text
ID: 2026
hash function: id % 10
2026 % 10 = 6
```

So value index 6-e যাবে।

---

## 2. Hash Function

Hash function key কে index-এ convert করে।

```text
key → hash function → index
```

Example:

```cpp
int hashFunction(int key, int tableSize) {
    return key % tableSize;
}
```

Good hash function-এর goal:

* Same key always same index দেবে
* Data evenly distribute করবে
* Too many collision হবে না

---

## 3. Collision কী?

দুইটা key same index দিলে collision হয়।

Example:

```text
table size = 10

25 % 10 = 5
35 % 10 = 5
```

25 and 35 both index 5-e যেতে চায়।

---

## 4. Collision Resolution

### Linear Probing

```text
index = (hash + i) % tableSize
```

Collision হলে next index check.

Example:

```text
25 goes to 5
35 also wants 5
5 busy → try 6
```

### Quadratic Probing

```text
index = (hash + i*i) % tableSize
```

More spread out.

### Double Hashing

```text
index = (h1(key) + i * h2(key)) % tableSize
```

Better distribution.

---

## 5. Hash Table with Linear Probing Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

class HashTable {
private:
    vector<int> table;
    int size;
    int EMPTY = -1;

public:
    HashTable(int s) {
        size = s;
        table.assign(size, EMPTY);
    }

    int hashFunction(int key) {
        return key % size;
    }

    void insert(int key) {
        int index = hashFunction(key);

        for (int i = 0; i < size; i++) {
            int newIndex = (index + i) % size;

            if (table[newIndex] == EMPTY) {
                table[newIndex] = key;
                return;
            }
        }

        cout << "Hash table is full" << endl;
    }

    bool search(int key) {
        int index = hashFunction(key);

        for (int i = 0; i < size; i++) {
            int newIndex = (index + i) % size;

            if (table[newIndex] == EMPTY) {
                return false;
            }

            if (table[newIndex] == key) {
                return true;
            }
        }

        return false;
    }

    void display() {
        for (int i = 0; i < size; i++) {
            cout << i << ": ";

            if (table[i] == EMPTY) {
                cout << "EMPTY";
            } else {
                cout << table[i];
            }

            cout << endl;
        }
    }
};

int main() {
    HashTable ht(10);

    ht.insert(25);
    ht.insert(35);
    ht.insert(15);
    ht.insert(7);

    ht.display();

    cout << "Search 35: " << ht.search(35) << endl;
    cout << "Search 99: " << ht.search(99) << endl;

    return 0;
}
```

Possible output:

```text
0: EMPTY
1: EMPTY
2: EMPTY
3: EMPTY
4: EMPTY
5: 25
6: 35
7: 15
8: 7
9: EMPTY
Search 35: 1
Search 99: 0
```

Explain:

```text
25 % 10 = 5
35 % 10 = 5 collision
so 35 goes to 6
15 % 10 = 5 collision
5 busy, 6 busy, so 15 goes to 7
7 % 10 = 7 collision
7 busy, so 7 goes to 8
```

---

# Final Revision Map for Student

তোমার class-er শেষে এই summary দিও:

```text
Linked List:
Node + next pointer
Insert, delete, search, traversal

Tree:
Hierarchical structure
Root, child, parent, leaf

BST:
Left smaller, right greater
Search/insert/delete

Traversal:
Preorder  = Root Left Right
Inorder   = Left Root Right
Postorder = Left Right Root
Level     = BFS style

Heap:
Complete binary tree
Max heap / Min heap
Priority queue

Graph:
Vertex + edge
BFS uses queue
DFS uses recursion/stack
Dijkstra = weighted shortest path
MST = minimum cost connection

Hashing:
Key → index
Collision handling
Linear, quadratic, double hashing
```

---

# তোমার Teaching Strategy

প্রতিটা topic শেখানোর সময় এই 5-step formula follow করো:

```text
1. Real-life example
2. Diagram
3. Core rule
4. Small code
5. Dry run
```

Example:

Linked list শেখানোর সময়:

```text
Real-life: train coach
Diagram: [10] -> [20] -> NULL
Rule: each node stores data and next address
Code: struct Node
Dry run: current = current->next
```

BST শেখানোর সময়:

```text
Real-life: sorted decision tree
Diagram: 50 root, 30 left, 70 right
Rule: left smaller, right greater
Code: insertBST
Dry run: insert 40
```

Graph শেখানোর সময়:

```text
Real-life: road map / friend network
Diagram: nodes and edges
Rule: adjacency list
Code: BFS/DFS
Dry run: queue/visited
```

---

# Final Class-er Best Ending

শেষে তাকে এটা বলো:

> “Programming ekhon pause hochhe, but eta stop na. Tomar math priority thakbe, karon Statistics, Data Science, ML—shob kichur base math. But ajker class-er por DSA-r main map tomar mathay thakbe. Future-e jodi programming, data analysis, ML, ba university course-e kono issue hoy, tumi amake janate parba. Ami joto tuku pari guide korbo.”

এতে সে confidence পাবে, আবার তুমি overpromise-ও করছো না।
