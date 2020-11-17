## 1. The more & operation we do, the smaller result we will get

1521 - https://leetcode.com/problems/find-a-value-of-a-mysterious-function-closest-to-target/

## 2. basic operation

a. check if is 1: mask & (1<<i) != 0  
b. check if is 0: mask & (1<<i) == 0  
c. set to 1: mask | (1<<i)  
d. set to 0: mask & ~(1<<i)
e. flip: mask ^ (1<<i)

## 3. get subsets from bit mask (by changing 1 to 0, so it means that we should start with all 1's and the target is all 0's

```python
cur = mask

while cur > 0:
  # remaining 1's
  remain = mask ^ cur # or mask - cur
  
  cur = (cur-1) & mask
```

1655 - https://leetcode.com/problems/distribute-repeating-integers/
