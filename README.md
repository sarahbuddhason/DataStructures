**Priority Queues**

- **Definition**: Data structure maintaining elements in order based on their priority. High-priority elements are served before lower ones.

- **Implementation**:
  - **Arrays/Linked Lists**: Inefficient for insertion/deletion.
  - **Binary Heaps**: Max-heap (high priority on top) or min-heap (low priority on top).
  - **Balanced Binary Search Trees**: Like AVL or Red-Black trees.
  - **Fibonacci Heaps**: Better average-case times for some operations.

- **Applications**:
  - **Dijkstra’s Shortest Path**.

- **Time Complexity** (Binary Heap):
  - **Insertion**: O(log n)
  - **Deletion**: O(log n)
  - **Building a heap**: O(n)

- **Space Complexity**: O(n).

```
#include <queue>

std::priority_queue<int> maxPQ; // Max Priority Queue
std::priority_queue<int, std::vector<int>, std::greater<int>> minPQ; // Min Priority Queue
```
