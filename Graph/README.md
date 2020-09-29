**1. BFS to get shortest path(steps) from one point to another**

For questions ask you to get smallest steps and you can move from current state to any state (need to know how to build the edges), you can try to use BFS to do the search

818 - https://leetcode.com/problems/race-car/

**2. When it gives you directed graph and you need to traverse the whole graph, convert to undirected graph and do a regular DFS traverse, and the the answer will emerge while traversing**

1466 - https://leetcode.com/problems/reorder-routes-to-make-all-paths-lead-to-the-city-zero/

**3. Floyd-Warshall**

calculate shortest path between all nodes

a. create |V| * |V| matrix M  
b. populate the M with edges (with weight)
```python
M = [[None] * n for _ in range(n)]]
for u, v, w in edges：
  M[u][v] = w
  M[u][u] = M[v][v] = 0

# basially use DP here to try all the paths between i and j, then find the shortest one among them
for k in range(n):
  for i in range(n):
    for j in range(n):
      if M[i][k] and M[k][j] and M[i][k] + M[k][j] < M[i][j]:
        M[i][j] = M[i][k] + M[k][j]
```
a viaration of Floyd-Warshall, since there is unique path for each i, j, just need to muptiply them together  
399 - https://leetcode.com/problems/evaluate-division/
