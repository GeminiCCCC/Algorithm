# LeetCode

review every week:

1. quick sort/merge sort  
912 - https://leetcode.com/problems/sort-an-array/  

2. number of sub arrays whose sum is K  
560 - https://leetcode.com/problems/subarray-sum-equals-k/

3. LIS  
300 - https://leetcode.com/problems/longest-increasing-subsequence/

4. Kadane  
53 - https://leetcode.com/problems/maximum-subarray/

5. max sum of subarray not greater than k
```python
sorted_presum = [0] # add 0 to handle empty list case
ans = -sys.maxsize
running_sum = 0

for num in arr:
  running_sum += num
  target_sum = running_sum - k
  index = bisect.bisect.left(sorted_presum, target_sum)
  
  if index < len(sorted_presum): # if index == len(sorted_presum) it means all the previous presum is smaller than the target, so no valid subarray whose sum is no greater than k
    ans = max(ans, running_sum - sorted_presum[index])
    
    if ans == k:
      return k
    
    bisect.insort(sorted_presum, running_sum)

return ans
```

6. get longest/shortest subarray whose sum is k

1658 - https://leetcode.com/problems/minimum-operations-to-reduce-x-to-zero/
