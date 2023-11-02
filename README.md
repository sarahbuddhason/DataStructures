# Data Structures

1. [Graph](#graph)
   - 1.1 [Adjacency Matrix](#adjacency-matrix)
   - 1.2 [Adjacency List](#adjacency-list)

2. [Priority Queue](#priority-queue)

3. [Heap](#heap)

4. [Linked List](#linked-list)

5. [Hash Table](#hash-table)

6. [Hash Map](#hash-map)

7. [Dictionary](#dictionary)

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
