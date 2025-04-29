# CMPS 2200 Assignment 5
## Answers

**Name:**Viraj Choksi





- **1a.** The maximum depth of a d-ary heap with n elements is O(log_d n), because each node has up to d children, so the height decreases as d increases.


- **1b.** Insert: Insert places the new element as the rightmost leaf and bubbles up by comparing with the parent. Each comparison is O(1) work, and there are at most O(log_d n) levels to traverse.
Thus, insert takes O(log_d n) work.
Delete-min:

Delete-min removes the root, moves the rightmost leaf to the root, and bubbles down to restore the heap property.
At each level, to find the minimum child requires O(d) comparisons, and there are O(log_d n) levels to traverse.
Thus, delete-min takes O(d log_d n) work.


- **1c.** Using a d-ary heap for Dijkstra's algorithm:
Each delete-min operation takes O(d log_d |V|) work and there are |V| delete-mins.
Each decrease-key (treated similarly to insert) takes O(log_d |V|) work and there are |E| decrease-keys.

Thus, the total work is: O(|V| d log_d |V| + |E| log_d |V|)


- **1d.** Suppose |E| = |V|^(1+ε) for some 0 < ε < 1.
We want the total work to be O(|E|).
Focus on the dominant term |V| d log_d |V| and require: |V| d log_d |V| <= c |V|^(1+ε) for constant c.

Thus, the best choice is: d = |V|^ε

This achieves overall work O(|E|).


- **2a.** Compute APSP(i, j, k), the shortest path from node i to node j using only intermediate nodes {0, 1, ..., k}. Do this incrementally for k = -1, 0, 1, 2.

k = -1: Only direct edges are allowed. So APSP(i, j, -1) is the weight of the direct edge from i to j if it exists, or ∞ otherwise. Diagonal entries (i = j) are 0.

k = 0: Now, paths are allowed to go through node 0. For each i, j: APSP(i, j, 0) = min(APSP(i, j, -1), APSP(i, 0, -1) + APSP(0, j, -1))

k = 1: Paths are allowed through nodes {0, 1}: APSP(i, j, 1) = min(APSP(i, j, 0), APSP(i, 1, 0) + APSP(1, j, 0))

k = 2: Now all nodes are allowed as intermediates. APSP(i, j, 2) = min(APSP(i, j, 1), APSP(i, 2, 1) + APSP(2, j, 1)). In this case, no new shorter paths are found, so values remain the same.


- **2b.** Yes, APSP(i, j, 2) can be written as: APSP(i, j, 2) = min(APSP(i, j, 1), APSP(i, 2, 1) + APSP(2, j, 1)). In other words, either the shortest path from i to j without using vertex 2, or a path that goes through vertex 2.


- **2c.** APSP(i, j, k) = min(APSP(i, j, k-1), APSP(i, k, k-1) + APSP(k, j, k-1)). The shortest path from i to j using vertices {0, ..., k} is either: the shortest path without using vertex k, or the shortest path from i to k, then from k to j.


- **2d.** Total number of distinct subproblems: O(n³), where n = number of vertices. Each subproblem is solved in O(1) work using memoization. Therefore, total work = O(n³).


- **2e.** Johnson's algorithm runs in O(VE + V log V) time with Fibonacci heaps, or O(VE log V) with binary heaps. Dynamic programming algorithm runs in O(V³) time. Dynamic programming is preferable when: the graph is dense (E ≈ V²), simpler code is needed, and negative edge weights are present (but no negative cycles). Johnson’s algorithm is preferable when: the graph is sparse (E ≪ V²), and faster performance is needed on large sparse graphs.



- **3a.** Yes, the MST is also a solution to the MMET. In an MST, if there were a spanning tree with a smaller maximum edge weight, then we could replace the largest edge in the MST with a smaller one, which would lead to a smaller total weight — contradicting the minimality of the MST. Thus, MST also minimizes the maximum edge weight.


- **3b.**
1. Compute the MST (call it T) using Kruskal's or Prim's algorithm.

2. For each edge e in T: Remove e from T, which splits it into two components, Find the minimum-weight edge e' not in T that reconnects these two components, Create a new tree by replacing e with e'.

3. Among all trees formed this way, choose the one with the minimum total weight. 


- **3c.** Building the MST takes O(|E| log |V|) using Kruskal’s algorithm with a union-find data structure.
For each edge in the MST (|V| - 1 edges):
Finding a replacement edge naively can take O(|E|) work per edge.
So overall work is O(|V| × |E|) to find all candidates.
Total work:
O(|E| log |V| + |V||E|).
