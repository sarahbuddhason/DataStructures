# Data Structures

1. [Graph](#graph)
   - 1.1 [Adjacency Matrix](#adjacency-matrix)
   - 1.2 [Adjacency List](#adjacency-list)

2. [Priority Queue](#priority-queue)

3. [Heap](#heap)

4. [Linked List](#linked-list)

5. [Hash Table](#hash-table)

6. [Hash Map](#hash-map)

7. [Hash Set](#hash-set)

8. [Dictionary](#dictionary)

9. [AVL Tree](#avl-tree)
   - 9.1 [Left Rotation (Right-Right Case)](#left-rotation-right-right-case)
   - 9.2 [Right Rotation (Left-Left Case)](#right-rotation-left-left-case)
   - 9.3 [Left-Right Rotation](#left-right-rotation)
   - 9.4 [Right-Left Rotation](#right-left-rotation)
   - 9.5 [Multiple Rotations](#multiple-rotations)

---

## Graph

### Adjacency Matrix

- **Representation**: 2D array of size VxV (where V is the number of vertices).
- `m[i][j] = 1` indicates an edge; otherwise, it's `0`.
- **Time**: O(1)
- **Space**: O(V^2)

```cpp
int V = 5;
vector<vector<int>> matrix(V, vector<int>(V, 0));

void addEdgeUndirected(int u, int v) {
    matrix[u][v] = 1;
    matrix[v][u] = 1;
}

void addEdgeDirected(int u, int v) {
    matrix[u][v] = 1;
}
```

### Adjacency List

- **Representation**: Array of lists, each of size V.
- `list[i]` contains all vertices adjacent to vertex i.
- **Time**: O(deg(v))
- **Space**: O(V + E)

```cpp
int V = 5;
vector<vector<int>> adjList(V);

void addEdgeUndirected(int u, int v) {
    adjList[u].push_back(v);
    adjList[v].push_back(u);
}

int V = 5;
vector<vector<int>> adjList(V);

void addEdgeDirected(int u, int v) {
    adjList[u].push_back(v);
}
```

---

## Priority Queue

- **Definition**: Maintains elements based on their priority. High-priority elements are dequeued before lower ones.
- **Implementation**:
  - Arrays/Linked Lists: Not efficient.
  - Binary Heaps: Max-heap or min-heap.
  - Balanced Binary Trees: AVL or Red-Black trees.
  - Fibonacci Heaps: Better average-case times for some operations.
- **Key Application**: Dijkstra’s Shortest Path.
- **Time (Using Binary Heap)**:
  - **Insertion**: O(log n)
  - **Deletion**: O(log n)
  - **Building a heap**: O(n)
- **Space**: O(n)

```cpp
#include <queue>

std::priority_queue<int> maxPQ; // Max Heap
std::priority_queue<int, std::vector<int>, std::greater<int>> minPQ; // Min Heap
```

---

## Heap

- **Definition**: A complete binary tree.
- **Types**: Max heap and min heap.
- **Applications**:
   - Priority Queues: To fetch the highest/lowest priority element.
   - Heap Sort: O(n log n).
   - Kth Largest/Smallest Element: O(n log n).
   - Merging K Sorted Lists: O(n log n).
   - Dijkstra's Algorithm: To select the closest vertex.
   - Load Balancing: For executing high-priority tasks.
- **Time**:
  - **Insertion**: O(log n)
  - **Pop**: O(log n)
  - **Peek**: O(1)
- **Space**: O(n)

---

## Linked List

- **Definition**: Linear structure of sequentially linked nodes.
- **Types**: Single Linked List (SLL) & Doubly Linked List (DLL).
- **Time (SLL)**:
  - **Insertion**: Head: O(1), Tail: O(n), Middle: O(n)
  - **Deletion**: Head: O(1), Tail: O(n), Middle: O(n)
  - **Access, Search**: O(n)
- **Time (DLL)**:
  - **Insertion**: Head: O(1), Tail: O(1), Middle: O(n)
  - **Deletion**: Head: O(1), Tail: O(1), Middle: O(n)
  - **Access, Search**: O(n)
- **Space**: O(n)

```cpp
void traverse(Node* head) {
    while (head) {
        std::cout << head->data << " ";
        head = head->next;
    }
}
```

---

## Hash Table

- **Definition**: Transforms data into a fixed-size array index via hashing.
- **Collisions**:
   - Arises when two distinct keys produce the same hash value. 
   - Resolutions are required for accurate data retrieval.
- **Chaining**:
   - A technique employed to handle collisions.
   - Each index maps to a list of values hashed to that index.
- **Applications**:
   - **Data Retrieval**: Fast lookups.
   - **Caching**: Store temporary data.
   - **Frequency Count**: Count items.
   - **Disjoint Set**: Track non-overlapping subsets.
   - **Substring Search**: Quickly find or match substrings.
   - **Unique Data**: Remove duplicates from a dataset.
   - **Associative Arrays**: Map keys to values.
- **Time**:
   - O(n) for collisions
   - O(1) otherwise
- **Space**: O(n)

```cpp
const int TABLE_SIZE = 100;

class HashTable {
    std::vector<std::list<int>> table;

public:
    HashTable() : table(TABLE_SIZE) {}

    int hashFunction(int key) {
        return key % TABLE_SIZE;
    }
    void insert(int key) {
        int index = hashFunction(key);
        table[index].push_back(key);
    }
    bool search(int key) {
        int index = hashFunction(key);
        for (int val : table[index]) {
            if (val == key) return true;
        }
        return false;
    }
    void remove(int key) {
        int index = hashFunction(key);
        table[index].remove(key);
    }
};
```

---

## Hash Map

- **Description**: Implementation of a hash table.
- **Time**:
   - O(n) for collisions
   - O(1) otherwise
- **Space**: O(n)

```cpp
#include <unordered_map> // A Hash Table

std::unordered_map<int, std::string> hashMap;
```

---

## Hash Set

- **Description**: Implementation of a hash table. Uses less memory than a hash map since no mappings.
- **Time**:
   - O(n) for collisions (bucket hashing)
   - O(1) otherwise
- **Space**: O(n)

```cpp
#include <unordered_set>

std::unordered_set<int> hashSet;
```

---

## Dictionary
- **Definition**: Collection of key-value pairs where keys are unique.
- **Time**:
   - O(n) for collisions
   - O(1) otherwise
- **Space**: O(n)

```cpp
#include <map> // A balanced BST, not a Hash Table

std::map<int, std::string> dict;
dict[1] = "one";
```

---

## AVL Tree

AVL trees are a type of self-balancing binary search tree. In an AVL tree, the heights of the two child subtrees of any node differ by at most one; if at any time they differ by more than one, rebalancing is done to restore this property.

The balance of a node is defined as the height of its right subtree minus the height of its left subtree. A node with balance +1, 0, or -1 is considered balanced. A node with balance +2 or -2 is unbalanced and requires rebalancing.

Here are the operations used to maintain the AVL property:

### Left Rotation (Right-Right Case)
A left rotation is used when a right-heavy subtree needs to be balanced, where the right child has a balance of 0 or +1 (right-right case).

1. The right child of the unbalanced node becomes the new root of the subtree.
2. The unbalanced node becomes the left child of the new root.
3. If the new root had a left child, it becomes the right child of the unbalanced node.

```cpp
Node* leftRotate(Node* x) {
    Node* y = x->right;
    Node* T2 = y->left;

    // Perform rotation
    y->left = x;
    x->right = T2;

    // Update heights
    x->height = max(height(x->left), height(x->right)) + 1;
    y->height = max(height(y->left), height(y->right)) + 1;

    // Return new root
    return y;
}
```

### Right Rotation (Left-Left Case)
A right rotation is used when a left-heavy subtree needs to be balanced, where the left child has a balance of 0 or -1 (left-left case).

1. The left child of the unbalanced node becomes the new root of the subtree.
2. The unbalanced node becomes the right child of the new root.
3. If the new root had a right child, it becomes the left child of the unbalanced node.

```cpp
Node* rightRotate(Node* y) {
    Node* x = y->left;
    Node* T2 = x->right;

    // Perform rotation
    x->right = y;
    y->left = T2;

    // Update heights
    y->height = max(height(y->left), height(y->right)) + 1;
    x->height = max(height(x->left), height(x->right)) + 1;

    // Return new root
    return x;
}
```

### Left-Right Rotation
A left-right rotation is a double rotation for the case when the left child of the unbalanced node has a right-heavy subtree. It is a combination of a left rotation on the left child, followed by a right rotation on the unbalanced node.

1. Perform a left rotation on the left child of the unbalanced node.
2. Perform a right rotation on the unbalanced node.

```cpp
Node* leftRightRotate(Node* z) {
    z->left = leftRotate(z->left);
    return rightRotate(z);
}
```

### Right-Left Rotation
A right-left rotation is a double rotation for the case when the right child of the unbalanced node has a left-heavy subtree. It is a combination of a right rotation on the right child, followed by a left rotation on the unbalanced node.

1. Perform a right rotation on the right child of the unbalanced node.
2. Perform a left rotation on the unbalanced node.

```cpp
Node* rightLeftRotate(Node* z) {
    z->right = rightRotate(z->right);
    return leftRotate(z);
}
```

### Multiple Rotations
1. If a subtree needs a **left rotation** to bring it into balance, first check the balance factor of the right child. If the right child is **left heavy** then do a **right rotation** on right child, followed by the original left rotation.
2. If a subtree needs a **right rotation** to bring it into balance, first check the balance factor of the left child. If the **left child** is **right heavy** then do a **left rotation** on the left child, followed by the original right rotation.

### Insertion

```cpp
#include <iostream>
#include <algorithm>

class Node {
public:
    int key;
    Node* left;
    Node* right;
    int height;

    Node(int k) : key(k), left(nullptr), right(nullptr), height(1) {}
};

class AVLTree {
public:
    // Utility: height of the tree
    int height(Node* N) {
        if (N == nullptr)
            return 0;
        return N->height;
    }

    // Utility: calculate the balance factor of a node
    int getBalance(Node* N) {
        if (N == nullptr)
            return 0;
        return height(N->right) - height(N->left);
    }

    Node* rightRotate(Node* root) {
        Node* new_root = root->left;
        Node* new_left = new_root->right;

        // Perform rotation
        new_root->right = root;
        root->left = new_left;

        // Update heights
        root->height = std::max(height(root->left), height(root->right)) + 1;
        new_root->height = std::max(height(new_root->left), height(new_root->right)) + 1;

        // Return new root
        return new_root;
    }

    Node* leftRotate(Node* root) {
        Node* new_root = root->right;
        Node* new_right = new_root->left;

        // Perform rotation
        new_root->left = root;
        root->right = new_right;

        // Update heights
        root->height = std::max(height(root->left), height(root->right)) + 1;
        new_root->height = std::max(height(new_root->left), height(new_root->right)) + 1;

        // Return new root
        return new_root;
    }

    Node* insert(Node* node, int key) {
        // Perform the normal BST insertion
        if (node == nullptr)
            return (new Node(key));

        if (key < node->key)
            node->left = insert(node->left, key);
        else if (key > node->key)
            node->right = insert(node->right, key);
        else
            return node;

        // Update the balance factor of this ancestor node
        node->height = std::max(height(node->left), height(node->right)) + 1;
        int balance = getBalance(node);

        // If this node becomes unbalanced, then there are 4 cases

        // Left Left Case
        if (balance < -1 && key < node->left->key)
            return rightRotate(node);

        // Right Right Case
        if (balance > 1 && key > node->right->key)
            return leftRotate(node);

        // Left Right Case
        // Node inserted into right subtree of left child of unbalanced node
        if (balance < -1 && key > node->left->key) {
            node->left = leftRotate(node->left);
            return rightRotate(node);
        }

        // Right Left Case
        // Node inserted into left subtree of right child of unbalanced node
        if (balance > 1 && key < node->right->key) {
            node->right = rightRotate(node->right);
            return leftRotate(node);
        }

        // Return the (unchanged) node pointer
        return node;
    }

    // A utility function to print the preorder traversal of the tree
    void preOrder(Node* root) {
        if (root != nullptr) {
            std::cout << root->key << " ";
            preOrder(root->left);
            preOrder(root->right);
        }
    }
};
```
