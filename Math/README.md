## 1. Calculate combination (within left and right set, the relative position cannot be changed)

a. (left+right)! // left! // right!, we can precalculate all factorials from 1 to (left+right)  
1569 - https://leetcode.com/problems/number-of-ways-to-reorder-array-to-get-same-bst/

## 2. use combination to check remaining possible string combination

1643 - https://leetcode.com/problems/kth-smallest-instructions/

## 3. calculate sum from n to n-k

```python
start = n
end = n - k - 1
start * (start+1) // 2 - end * (end+1) // 2
```

1648 - https://leetcode.com/problems/sell-diminishing-valued-colored-balls/

## 4. gcd

```python
def gcd(a, b):
  # Unless b == 0, the result will have the same sign as b
  while b:
    a, b = b, a % b
  
  return a  
```
