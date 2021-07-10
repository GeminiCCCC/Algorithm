## 1. BFS to get shortest path(steps) from one point to another

For questions ask you to get smallest steps and you can move from current state to any state (need to know how to build the edges), you can try to use BFS to do the search

818 - https://leetcode.com/problems/race-car/

## 2. When it gives you directed graph and you need to traverse the whole graph, convert to undirected graph and do a regular DFS traverse, and the the answer will emerge while traversing

1466 - https://leetcode.com/problems/reorder-routes-to-make-all-paths-lead-to-the-city-zero/

## 3. Floyd-Warshall

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
a viaration of Floyd-Warshall, since there is unique path for each i, j, just need to multiply them together  
399 - https://leetcode.com/problems/evaluate-division/

## 4. get all sub trees given nodes and edges

try all the nodes combinations  0 ~ 2^n, and then use bitmask + BFS/DFS to check if can connect all the nodes  
1617 - https://leetcode.com/problems/count-subtrees-with-max-distance-between-cities/

## 5. how to calculate tree diameter

1. try each node as starting point, then do BFS to get farthest node and update the max_distance  
2. use any node as starting point, do BFS/DFS to find farthest node far1, then use far1 as starting point do another BFS/DFS to find farthest node far2, then do a third BFS/DFS to get the distance between far1 and far2 which will be the tree diameter, I prefer BFS  
1617 - https://leetcode.com/problems/count-subtrees-with-max-distance-between-cities/

## 6. 2D board can also be treated as graph when you can move in 4 directions, and when it asks you to find the min from start to end, it's time to use Dijkstra

1631 - https://leetcode.com/problems/path-with-minimum-effort/

## 7. find bridge in graph - tarjan's algorithm

1. start from any node do dfs
2. assign each unvisited node a label
3. for current node u and each neighbor v, if dfs(v) returns a label <= curLabel, edge (u,v) is part of a cycle and can be removed
4. the edges didn't get removed are the bridge

1192 - https://leetcode.com/problems/critical-connections-in-a-network/

## 8. Travelling salesman problem - TSP, minimum cost to visit each node once  
use bit mask 

943 - https://leetcode.com/problems/find-the-shortest-superstring/

## 9. Cycle detection in directed graph  
-1 - not visited  
0 - being processed (including all the children nodes)  
1 - processed (including all the children nodes)  

if any neighbor is 0, then found cycle  

1059 - https://leetcode.com/problems/all-paths-from-source-lead-to-destination/

## 10. Dilkistra is to improve the cost for each node, no need to maintain visited set, and if there is 2nd contraint, will need to improve both

1928 - https://leetcode.com/problems/minimum-cost-to-reach-destination-in-time/
