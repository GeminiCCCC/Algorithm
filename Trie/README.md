## 1. construct Trie with reversed word to handle letter stream problem

1032 - https://leetcode.com/problems/stream-of-characters/

## 2. use Trie to get max xor with a group of numbers

each node has two child nodes (has 0 or 1 value), and each node also has cnt indicates if there is any 0 or 1 number for the current node because there is also delete operation. And when query xor for x, starts from root and look for the opposite value of x. If target number exists in the path then add the current value of the bit, else go the the other number path  
https://codeforces.com/problemset/problem/706/D
