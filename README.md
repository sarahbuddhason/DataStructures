## Graphs

### Adjacency Matrix

- Representation: 2D array of size VxV (where V is the number of vertices).
- `m[i][j] = 1` indicates an edge; otherwise, it's `0`.
- **Space**: O(V^2)
- **Access/Check Edge**: O(1)

```cpp
int V = 5;
vector<vector<int>> matrix(V, vector<int>(V, 0));

void addEdgeUndirected(int u, int v) {
    matrix[u][v] = 1;
    matrix[v][u] = 1;
}

int V = 5;
vector<vector<int>> matrix(V, vector<int>(V, 0));

void addEdgeDirected(int u, int v) {
    matrix[u][v] = 1;
}
```

### Adjacency List

- Representation: Array of lists, each of size V.
- `list[i]` contains all vertices adjacent to vertex i.
- **Space**: O(V + E)
- **Access/Check Edge**: O(deg(v))

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
