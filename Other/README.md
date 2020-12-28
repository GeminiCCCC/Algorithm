## 1. Merge range length

get left_length = lengths[num-1] and right_length = lengths[num+1], new length is left + right + 1, and only needs to update lengths[num-left] = lengths[num+right] = new_length

128 - https://leetcode.com/problems/longest-consecutive-sequence/  also needs to update the length for the number itself since num could be duplicated  
1562 - https://leetcode.com/problems/find-latest-group-of-size-m/

## 2. 2D (m * n) pre_sum

```python
pre_sum = [[0] * (n+1) for _ in range(m+1) # pad +1 to handle border element

for i in range(m-1, -1, -1):
  for j in range(n-1, -1, -1):
    pre_sum[i][j] = nums[i][j] + pre_sum[i+1][j] + pre_sum[i][j+1] - pre_sum[i+1][j+1]
    
# to use pre_sum to calculate length of l square's sum
sum = pre_sum[i][j] - pre_sum[i+l][j] - pre_sum[i][j+l] + pre_sum[i+l][j+l]

```

1292 - https://leetcode.com/problems/maximum-side-length-of-a-square-with-sum-less-than-or-equal-to-threshold/

## 3. How to settle debts between people with min transactions?

use DFS + Backtracking with person idx as parameter, for current person (idx), find the next person whose debt has opposite sign and always clear the current person's debt and then move the idx forward by one, because after the current transaction, 0 - idx are all settled, so that we can simply keep going forward. And the base case is when idx == n which means everyone is settled  
465 - https://leetcode.com/problems/optimal-account-balancing/

## 4. When see a start - end event with a value of it, separate it into two events, (start, value) and (end, -value), then sort by timestamp

1094 - https://leetcode.com/problems/car-pooling/

## 5. marking number in array to its negative version is a good way of flagging the number while keep the number's value, we usually use this technique to get O(1) space

41 - https://leetcode.com/problems/first-missing-positive/

## 6. Gray Code - two successive values differ in only one bit

```python
ans = []

for i in range(1<<n):
  ans.append(i^(i>>1))
  
return ans

```

89 - https://leetcode.com/problems/gray-code/

use reverse gray code to get result  
1611 - https://leetcode.com/problems/minimum-one-bit-operations-to-make-integers-zero/

## 7 when try all possible scenarios in BFS/DP etc, try to reduce the invalid scenarios

find first not matched letter and then only make swap when the other letter is a valid option (not already matched with B[j] and match with B[i]  
854 - https://leetcode.com/problems/k-similar-strings/

## 8 when there are multiple conditions need to be meet, try to pre process to get result for one condition first.

456 - https://leetcode.com/problems/132-pattern/

## 9 calculate ranking based on the value

1331 - https://leetcode.com/problems/rank-transform-of-an-array/  
1632 - https://leetcode.com/problems/rank-transform-of-a-matrix/

## 10 below trick can convert "minimum moves to make sth consecutive" to "minimum moves to make sth into a single point"

```python
pos = [pos[i]-i for i in range(pos)] 
```
https://leetcode.com/problems/minimum-adjacent-swaps-for-k-consecutive-ones/
