## 1. Use Fenwick Tree to quickly update and get the pre_sum values, since normal way updating the pre_sum will take O(n) time, and with Fenwick Tree only takes O(logn). 
Problem 315 uses Fenwick Tree to maintain the smaller number for each number so far (traverse from end to start), and every time we have new number being added to the front, we just need to find all the numbers which are smaller than it and sum all the smaller numbers and its smallerCount.
With Fenwick Tree we improve the time complexity from O(n^2) brutal force to O(nlogn) i.e loop through each number o(n) and for each number, search the Tree (logn)

315 - https://leetcode.com/problems/count-of-smaller-numbers-after-self/

## 2. use BIT to find how many elements on my left/right side when inserting
```python
tree = [0] * (n+1)

def update(i, k):
  while i <= n:
    tree[i] += k
    i += i & -i

def getSum(i):
  ans = 0
  while i > 0:
    ans += tree[i]
    i -= i & -i
  
  return ans
```

1649 - https://leetcode.com/problems/create-sorted-array-through-instructions/

## 3. use Fenwick Tree to find how many index has count smaller than the current index count

a. get count for each index i  
b. loop from right to left, freq[i] is the freqency for the current index number to the left. At the moment fenwick tree stores the count for each number(same number with different index will increase the number in fenwick tree, the index of ft[] is the number value, and the value of ft[] is the freqency for the number so far from right side) from right side to the current i. So for the current i we need to find how many indices on the right side (everything in the fenwick ATM) has count smaller than freq[i], which is the sum range from 1 to freq[i]-1 in the fenwick tree  
c. increase the cnt and update fenwick tree for the next i  
https://codeforces.com/problemset/problem/459/D
