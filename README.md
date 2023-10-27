## Graph

**1. Adjacency Matrix**
- 2D array of size VxV (V: number of vertices).
- `m[i][j] = 1` if there's an edge, otherwise `0`.
- **Space**: O(V^2)
- **Access/Check Edge**: O(1)

```
int V = 5;
vector<vector<int>> matrix(V, vector<int>(V, 0));

// Add edge from vertex u to vertex v
void addEdge(int u, int v) {
    matrix[u][v] = 1;
    matrix[v][u] = 1;  // For undirected graph
}
```

**2. Adjacency List**
- Array of lists of size V.
- `list[i]` stores all vertices adjacent to vertex i.
- **Space**: O(V + E)
- **Access/Check Edge**: O(deg(v))

```
int V = 5;
vector<vector<int>> adjList(V);

// Add edge from vertex u to vertex v
void addEdge(int u, int v) {
    adjList[u].push_back(v);
    adjList[v].push_back(u);  // For undirected graph
}
```

---

## Priority Queue

- **Definition**: Data structure maintaining elements in order based on their priority. High-priority elements are served before lower ones.

- **Implementation**:
  - **Arrays/Linked Lists**: Inefficient for insertion/deletion.
  - **Binary Heaps**: Max-heap (high priority on top) or min-heap (low priority on top).
  - **Balanced Binary Search Trees**: Like AVL or Red-Black trees.
  - **Fibonacci Heaps**: Better average-case times for some operations.

- **Applications**:
  - **Dijkstra’s Shortest Path**.

- **Time** (Binary Heap):
  - **Insertion**: O(log n)
  - **Deletion**: O(log n)
  - **Building a heap**: O(n)

- **Space**: O(n).

```
#include <queue>

std::priority_queue<int> maxPQ; // Max Priority Queue
std::priority_queue<int, std::vector<int>, std::greater<int>> minPQ; // Min Priority Queue
```
