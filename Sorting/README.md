**1. quick sort**
```python
def partition(nums, low, high):
  i = low
  pivot = nums[high]
  
  for j in range(low, high):
    # move all numbers smaller than pivot to the front
    if nums[j] < pivot:
      nums[i], nums[j] = nums[j], nums[i]
      i += 1
  
  # at this point i is the first number that greater than pivot, so we move the pivot to the correct position, and return the partition point
  nums[i], nums[high] = nums[high], nums[i]
  
  return i
  
def quickSort(nums, low, high):
  if low < high:
    pi = partition(nums, low, high)
    
    quickSort(nums, low, pi-1)
    quickSort(nums, pi+1, high)

```

**2. every time when asks you to find a pair or triplet whos sum satifies a condition, always try to sort the list and then use two pointer to solve it**

259 - https://leetcode.com/problems/3sum-smaller/
