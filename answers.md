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

k = 0: Now, paths are allowed to go through node 0. 

k = 1: Paths are allowed through nodes {0, 1}.

k = 2: Now all nodes are allowed as intermediates. In this case, no new shorter paths are found, so values remain the same.


- **2b.**


- **2c.**

- **2d.**

- **2e.**



- **3a.**


- **3b.**


- **3c.**
