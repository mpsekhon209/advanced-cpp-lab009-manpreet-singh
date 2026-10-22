# Max-Heap Complexity Analysis

For a heap containing $n$ elements, the array representation stores the root at index $0$. For a node at index $i$, its parent is at $\lfloor(i-1)/2\rfloor$, its left child is at $2i+1$, and its right child is at $2i+2$. The max-heap property requires every parent to be greater than or equal to its children, so the maximum is always at the root.

| Operation | Time complexity | Extra space |
| --- | ---: | ---: |
| `top` / `empty` / `size` | $O(1)$ | $O(1)$ |
| `contains` | $O(n)$ | $O(1)$ |
| `push` | $O(\log n)$ | $O(1)$ auxiliary |
| `pop` | $O(\log n)$ | $O(1)$ auxiliary |
| `buildHeap` | $O(n)$ | $O(1)$ auxiliary beyond stored vector |
| `heapSort` | $O(n\log n)$ | $O(n)$ output |

Insertion appends an item and sifts it toward the root; extraction moves the last item to the root and sifts it downward. Both paths cross at most the heap height, which is $O(\log n)$ because the tree is complete. Bottom-up construction sifts internal nodes downward, taking $O(n)$ total time rather than inserting every item separately in $O(n\log n)$. Heap sort repeatedly extracts the maximum and reverses the descending extraction order to return ascending values. This implementation consumes the heap while sorting.

A heap is preferable when the workload repeatedly needs the current minimum or maximum, such as priority queues and scheduling. It is less suitable for arbitrary membership checks because it has no ordering between unrelated branches, so search is linear. A sorted vector permits $O(\log n)$ binary-search lookup but insertion/removal can take $O(n)$ due to shifting. A balanced BST supports ordered lookup, insertion, deletion, and range traversal in $O(\log n)$, but uses per-node links and more memory; a heap offers compact array storage and fast access to one priority extreme.