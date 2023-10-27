# Data Structures

1. [Graphs](#graphs)
   1.1 [Adjacency Matrix](#adjacency-matrix)
   1.2 [Adjacency List](#adjacency-list)

2. [Priority Queue](#priority-queue)

3. [Heap](#heap)

4. [Linked Lists](#linked-lists)

5. [Hash Table](#hash-table)

6. [Hash Map](#hash-map)

---

## Graphs

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

- **Definition**: A data structure that maintains elements based on their priority. High-priority elements are dequeued before lower ones.
- **Implementation**:
  - Arrays/Linked Lists: Not efficient for insertion/deletion.
  - Binary Heaps: Can be max-heap (high priority on top) or min-heap (low priority on top).
  - Balanced Binary Search Trees: Such as AVL or Red-Black trees.
  - Fibonacci Heaps: Have better average-case times for certain operations.
- **Applications**:
  - Dijkstra’s Shortest Path.
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

- **Description**: A complete binary tree.
- **Types**: Mainly max heap and min heap.
- **Use**: Often used for implementing priority queues.
- **Applications**:
  1. Priority Queues: To fetch the highest/lowest priority element.
  2. Heap Sort: To sort in O(n log n) time.
  3. Kth Largest/Smallest Element: Done in O(n log k) time.
  4. Merging K Sorted Lists: Achieved in O(n log k) time.
  5. Dijkstra's Algorithm: To select the closest vertex.
  6. Load Balancing: For executing high-priority tasks.
- **Time**:
  - **Insertion**: O(log n)
  - **Pop**: O(log n)
  - **Peek**: O(1)
- **Space**: O(n)

---

## Linked Lists

- **Description**: A linear data structure comprised of nodes linked sequentially.
- **Types**: Single Linked List (SLL) & Doubly Linked List (DLL).
- **Time (SLL)**:
  - **Insertion**: Head: O(1), Tail: O(n), Middle: O(n)
  - **Deletion**: Head: O(1), Tail: O(n), Middle: O(n)
  - **Access/Search**: O(n)
- **Time (DLL)**:
  - **Insertion**: Head: O(1), Tail: O(1), Middle: O(n)
  - **Deletion**: Head: O(1), Tail: O(1), Middle: O(n)
  - **Access/Search**: O(n)
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

- **Description**: Conversion of data into a fixed-size array index (hashing).
  
**Collisions**:
- Occurrences when two distinct keys produce the same hash value. 
- Resolutions are required for accurate data retrieval.

**Chaining**:
- A technique employed to handle collisions.
- Each index in the table points to a list of all values that hash to that specific index.

**Applications**:

- **Data Retrieval**: Fast lookups (e.g., database indexing).
- **Caching**: Store temporary data (e.g., web server cache).
- **Frequency Count**: Count items (e.g., character frequency in strings).
- **Disjoint Set**: Track non-overlapping subsets (e.g., network connectivity).
- **Substring Search**: Quickly find or match substrings (e.g., in text analysis).
- **Unique Data**: Remove duplicates from a dataset.
- **Associative Arrays**: Map keys to values (e.g., dictionary implementations).

**Time**:
- O(n) for collisions
- O(1) otherwise

**Space**: O(n)

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

##Hash Map

- Implementation of a hash table.

**Time**:
- O(n) for collisions
- O(1) otherwise

**Space**: O(n)

```cpp
#include <unordered_map> // A Hash Table

std::unordered_map<int, std::string> hashMap;
```

---

**Dictionaries**:
- Collection of key-value pairs.
- Keys are unique.

**Time**:
- O(n) for collisions
- O(1) otherwise

**Space**: O(n)

```cpp
#include <map> // A balanced BST, not a Hash Table

std::map<int, std::string> dict;
dict[1] = "one";
```
