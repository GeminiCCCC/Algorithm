**1. Permutation**

a. Permutation cares about ordering  
b. total number of distinct permutation is n!  
c. total number of duplicate allowed permutation is n^n (n is the length of arr)

```python
def permutate(self, nums):
  ans = []
  
  n = len(nums)
  
  def backTrack(start):
    if start == n:
      ans.append(nums[:])
      
      for i in range(start, n):
        nums[start], nums[i] = nums[i], nums[start]
        backTrack(start+1)
        nums[start], nums[i] = nums[i], nums[start]
  
  permutate(0)
  
  return ans

```

**2. Combination**

a. Combination does not care about ordering  
b. n! // k! // (n-k)! or (left+right)! // left! // right!  
1569 - https://leetcode.com/problems/number-of-ways-to-reorder-array-to-get-same-bst/
