## 1. Permutation

a. Permutation cares about ordering  
b. total number of distinct permutation is n!  
c. total number of duplicate allowed permutation is n^n (n is the length of arr)  
d. permutation with duplicate nums: n!//cnt[num1]! * cnt[num2]!*...*cnt[numk]!

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

## 2. Combination

a. Combination does not care about ordering  
b. n! // k! // (n-k)! or (left+right)! // left! // right!  
1569 - https://leetcode.com/problems/number-of-ways-to-reorder-array-to-get-same-bst/

## 3. calculate factorial with modulo
n! // k! = fact[n] * invFact[k]

```python
fact = [0] * n
invFact = [0] * n
fact[0] = 1
invFact[0] = pow(1, mod-2, mod)

for i in range(1, n):
    fact[i] = (i * fact[i-1]) % mod
    invFact[i] = pow(fact[i], mod-2, mod)
```
