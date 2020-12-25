## 1. Mo's Algorithm O(n*sqrt(n))

From q(l, r) if you can get q(l-1, r), q(l, r+1), q(l+1, r), q(l, r-1) in O(1), use Mo's Algorithm.

1. assign each q(l, r) to a block with size sqrt(n)  
2. sort query with block index and then r  
3. calculate each q from previous q, the complexity for each query is the shortest manhattan distance |l-l'| + |r-r'|   
https://codeforces.com/problemset/problem/617/E
