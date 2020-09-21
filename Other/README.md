**1. Merge range length**

get left_length = lengths[num-1] and right_length = lengths[num+1], new length is left + right + 1, and only needs to update lengths[num-left] = lengths[num+right] = new_length

128 - https://leetcode.com/problems/longest-consecutive-sequence/  
1562 - https://leetcode.com/problems/find-latest-group-of-size-m/

**2. 2D (m * n) pre_sum**

```python
pre_sum = [[0] * (n+1) for _ in range(m+1) # pad +1 to handle border element

for i in range(m-1, -1, -1):
  for j in range(n-1, -1, -1):
    pre_sum[i][j] = nums[i][j] + pre_sum[i+1][j] + pre_sum[i][j+1] - pre_sum[i+1][j+1]
    
# to use pre_sum to calculate length of l square's sum
sum = pre_sum[i][j] - pre_sum[i+l][j] - pre_sum[i][j+l] + pre_sum[i+l][j+l]

```

1292 - https://leetcode.com/problems/maximum-side-length-of-a-square-with-sum-less-than-or-equal-to-threshold/

**3. How to settle debts between people with min transactions?**

use DFS + Backtracking with person idx as parameter, for current person (idx), find the next person whose debt has opposite sign and always clear the current person's debt and then move the idx forward by one, because after the current transaction, 0 - idx are all settled, so that we can simply keep going forward. And the base case is when idx == n which means everyone is settled  
465 - https://leetcode.com/problems/optimal-account-balancing/

**4. When see a start - end event with a value of it, separate it into two events, (start, value) and (end, -value), then sort by timestamp**

1094 - https://leetcode.com/problems/car-pooling/
