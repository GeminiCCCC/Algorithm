# LeetCode

review every week:

## 1. quick sort/merge sort  
912 - https://leetcode.com/problems/sort-an-array/  

## 2. number of sub arrays whose sum is K  
560 - https://leetcode.com/problems/subarray-sum-equals-k/

## 3. LIS  
300 - https://leetcode.com/problems/longest-increasing-subsequence/

## 4. Kadane  
53 - https://leetcode.com/problems/maximum-subarray/

## 5. max sum of subarray not greater than k
```python
sorted_presum = [0] # add 0 to handle empty list case
ans = -sys.maxsize
running_sum = 0

for num in arr:
  running_sum += num
  target_sum = running_sum - k
  index = bisect_left(sorted_presum, target_sum)
  
  if index < len(sorted_presum): # if index == len(sorted_presum) it means all the previous presum is smaller than the target, so no valid subarray whose sum is no greater than k
    ans = max(ans, running_sum - sorted_presum[index])
    
    if ans == k:
      return k
    
    bisect.insort(sorted_presum, running_sum)

return ans
```

## 6. get longest/shortest subarray whose sum is k

325 - https://leetcode.com/problems/maximum-size-subarray-sum-equals-k/  
1658 - https://leetcode.com/problems/minimum-operations-to-reduce-x-to-zero/

## 7. how to search rotated array:

81 - https://leetcode.com/problems/search-in-rotated-sorted-array-ii/

## 8. calculator:

227 - https://leetcode.com/problems/basic-calculator-ii/

## 9. Dijkstra:

1631 - https://leetcode.com/problems/path-with-minimum-effort/

## 10. Knapsack

416 - https://leetcode.com/problems/partition-equal-subset-sum/ 01  
https://codeforces.com/problemset/problem/1381/B 01  
322 - https://leetcode.com/problems/coin-change/ complete

## 11. Fenwick Tree

https://codeforces.com/problemset/problem/459/D

## 12. gcd

```python
def gcd(a, b):
  # Unless b == 0, the result will have the same sign as b
  while b:
    a, b = b, a % b
  
  return a  
```

## 13. preprocess from left and right, then loop through each location and use left and right array to get the min/max answer

1671 - https://leetcode.com/problems/minimum-number-of-removals-to-make-mountain-array/  
https://codeforces.com/problemset/problem/1409/E

## 14. given queries and a condition, return the ans for each query. Usually sort the queries and the other values. and build the data from smallest to biggest, every time we only use the numbers satisfied the current query.

1697 - https://leetcode.com/problems/checking-existence-of-edge-length-limited-paths/  
1707 - https://leetcode.com/problems/maximum-xor-with-an-element-from-array/

## 15. use binary search to find the array's shortest and longest length

1712 - https://leetcode.com/problems/ways-to-split-array-into-three-subarrays/  

## 16. LCS to LIS

when one array has distinct value, LCS can be converted to LIS and solved in O(nlogn)  
1713 - https://leetcode.com/problems/minimum-operations-to-make-a-subsequence/  
1143 - https://leetcode.com/problems/longest-common-subsequence/
