## 1. quick sort nlogn
```python
def quickSort(nums):
  def sort(left, right):
    if left < right:
      pivot = partition(left, right)

      sort(left, pivot-1)
      sort(pivot+1, right)
      
  # partition moves pivot to the correct position, all numbers on the left is smaller than pivot
  def partition(left, right):
    pivot = nums[right]
    i = left
    for j in range(left, right):
      # move all numbers smaller than pivot to the front
      if nums[j] < pivot:
        nums[i], nums[j] = nums[j], nums[i]
        i += 1
    
    # at this point i is the first number that greater than pivot, so we move the pivot to the correct position, and return the partition point
    nums[i], nums[right] = nums[right], nums[i]
    
    return i
 
  sort(0, len(nums)-1)
```

## 2. merge sort nlogn
```python
def mergeSort(nums):
  def partition(cur_nums):
    n = len(cur_nums)
    
    if n == 1:
      return cur_nums
    
    mid = n // 2
    arr1 = partition(cur_nums[:mid])
    arr2 = partition(cur_nums[mid:])
    
    return merge(arr1, arr2)
      
  
  def merge(arr1, arr2):
    p1 = p2 = 0
    n1 = len(arr1)
    n2 = len(arr2)
    ans = []
    
    while p1 < n1 and p2 < n2:
      if arr1[p1] < arr2[p2]:
        ans.append(arr1[p1])
        p1 += 1
      else:
        ans.append(arr2[p2])
        p2 += 1
    
    if p1 < n1:
      ans.extend(arr1[p1:])
    if p2 < n2:
      ans.extend(arr2[p2:])
    
    return ans
    
  return partition(nums)
```

**2. every time when asks you to find a pair or triplet whos sum satifies a condition, always try to sort the list and then use two pointer to solve it**

259 - https://leetcode.com/problems/3sum-smaller/
