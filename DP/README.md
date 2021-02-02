## 1. min-max problem

How can you tell it's a min_max problem? 

1) Two players. 
2) Take turns 
3) Both play optimally

Use max relative score (max winning score) to solve it, and traverse from end. And the reason we can traverse from the end is becasue there are constant k ways of taking stones for each player (1460). If the k is changing based on the previous player, then we can do bottom up DP, we have to use top down recursive dp. (1140)

And once we get the final answer for the most scores player A can win against player B,  dp(0) in this case, we can calculate the actual score for A and B,  A = (total + max_winning_against_B) // 2,   B = total - A

1460 - https://leetcode.com/problems/stone-game-iii/

1140 - https://leetcode.com/problems/stone-game-ii/

1.1 another kind of min max problem

375 - https://leetcode.com/problems/guess-number-higher-or-lower-ii/

## 2. dp + graph (edges are the possible scenarios at current state)

568 - https://leetcode.com/problems/maximum-vacation-days/

## 3. For problem that has two moving points, then need to have three/four dimension dp, and for the problem start from one point and the stop point is not fixed, then top down DP is better

741 - https://leetcode.com/problems/cherry-pickup/ # for cherry pick problems: 1. when two people on the same cell, only collect cherry once. 2 use -sys.maxsize to indicate invalid path

1463 - https://leetcode.com/problems/cherry-pickup-ii/

1320 - https://leetcode.com/problems/minimum-distance-to-type-a-word-using-two-fingers/

## 4. String DP problems

4.1 singe string: with in a range, split the range into all possible two sub strings, and calculate the first substring result(find a way to calculate the optimal result) and use dp to calculate the rest substring

1531 - https://leetcode.com/problems/string-compression-ii/

## 5. DP to calculate all possible ways with 2D pre sum, 2D pre sum is the way to get counts with in a sub 2D matrix

1444 - https://leetcode.com/problems/number-of-ways-of-cutting-a-pizza/

## 6. Buy and Sell Stock problems, always use buy[i] and sell[i] to store: by index i and last transaction was buy/sell, what's the max profit. And the answer is sell[n-1]

309 - https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/

if you only allow to do k transactions, then need to have 2nd dimension for buy and sell dp array, buy[i][k] = for the first ith prices, last action was buy and with at most k transactions. And notice that to calculate sell[i][k], we should use buy[i-1][k], not buy[i-1][k-1] becasue buy stock/sell stock is considered as one transaction.

123 - https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/
188 - https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/


## 7. knapsack

7.1 0-1

dp[i][j] = with first ith items, and with most j capacity, the max value it can get(the last part could be differ based on different problems)

```python
for i in range(1, n+1) # n is the length of items
  w, v = items[i-1] # w is item weight, v is item value
  for j in range(c+1) # c is the total capacity of the bag 
    dp[i][j] = dp[i-1][j] # not using ith item
    
    if j >= w:
      # v is the value of the current item
      # and we use dp[i-1] here becasue one item can only be picked once, so when calculate dp for ith item we need to rely on the i-1 which is the state that no ith item had been picked yet
      dp[i][j] = max(dp[i][j], dp[i-1][j-w] + v) 
      
# since we initialize all dp element with 0, the dp[n][c] can include both exact c and less than c case, if we only want to check exact c capacity, then we only initialize dp[0] = 0, and all the other dp[i] = -sys.maxsize
return dp[n][c] 
```

we can improve dp[i][j] to dp[j] since dp[i][j] only relies on dp[i-1]

```python
for i in range(1, n+1) # n is the length of items
  w, v = items[i-1] # w is item weight, v is item value
  # when calculating dp for ith item, we want to use the dp value from i-1 th state, we need to loop from biggest to smallest (so that when we calculate dp[j], the dp[j-w] had not been calculated for the current ith, it's still has the value from dp[i-1]
  for j in range(c, w-1,-1)
      dp[j] = max(dp[j], dp[j-w] + v) 

return dp[c] 
```
494 - https://leetcode.com/problems/target-sum/ how to convert positive/negative number to 0-1 knapsack

416 - https://leetcode.com/problems/partition-equal-subset-sum/

871 - https://leetcode.com/problems/minimum-number-of-refueling-stops/ variation of 0-1 knapsack

7.1.1 2D 0-1:

Have two capacities value, just need to define 2D dp array and for each item, get weight for each capacity

474 - https://leetcode.com/problems/ones-and-zeroes/

7.2 complete

```python
for i in range(1, n+1)
  w, v = items[i-1]
  for j in range(c+1)
    dp[i][j] = dp[i-1][j]
    
    if j >= w:
      # the only difference with 0-1 knapsack is that we need to use dp[i][j-w] which means we have alreay considered picking the ith item when calculating dp[i][j]
      dp[i][j] = max(dp[i][j], dp[i][j-w] + v) 

return dp[n][c] 
```

we can improve dp[i][j] to dp[j] since dp[i][j] only relies on dp[i-1]

```python
for i in range(1, n+1)
  w, v = items[i-1]
  # for complete knapsack since we want to consider ith item, we should loop from smallest to biggest so that then calculate dp[j], the dp[j-w] had already been calculated
  for j in range(w, c+1)
      dp[j] = max(dp[j], dp[j-w] + v) 

return dp[c] 
```

322 - https://leetcode.com/problems/coin-change/

## 8. Bit trick + DP

To union two sets of items, we can convert each set to its binary format and do | for two sets  
1125 - https://leetcode.com/problems/smallest-sufficient-team/

if list size is < 32, then use bit mask to mark the status of list of items (mask | 1 << i), because it's hard to check the status of each item and if use top down dp, it cannot hash list/set. When to check if the item's bit value is set (0 or 1), use mask & 1 << i == 0  
1595 - https://leetcode.com/problems/minimum-cost-to-connect-two-groups-of-points/

whenever we need to check the state of list of items, use bit mask to check all of them in O(1) time  
1434 - https://leetcode.com/problems/number-of-ways-to-wear-different-hats-to-each-other/

## 9. Current color/number cannot be the same as previous one( or can only has k consecutive times)

for k consecutive times, we will need to add another dimension for k. And when k = 1 this is the special case, it means that we can get to k=1 from all previous state as long as the current number is not the same as previous number

1223 - https://leetcode.com/problems/dice-roll-simulation/

## 10. minimum swaps to make two list strictly increasing

A[i] > A[i-1] and B[i] > B[i-1]  
A[i] > B[i-1] and B[i] > A[i-1]

need to use two dp arrays, swap[i] and not_swap[i], because swap/not_swap will have different impact (similar like stocks problems, sell/not sell)  
801 - https://leetcode.com/problems/minimum-swaps-to-make-sequences-increasing/

another swap or not swap problem  
https://codeforces.com/problemset/problem/706/C

## 11. greedy + dp

1553 - https://leetcode.com/problems/minimum-number-of-days-to-eat-n-oranges/

## 12. Palindrome

Longest Palindrom substring:

dp[i][j] means true/false if i...j is palindrom

dp[i][j] = true if s[i] == s[j] and (j-i < 3 or dp[i+1][j-1] = true  
and if dp[i][j] is true, update the result if j-i+1 > ans  
5 - https://leetcode.com/problems/longest-palindromic-substring/solution/

Longest Palindrome subsequence: 

dp[i][j] means the longest subsequence length so far
dp[i][j] = 0/1 when s[i] == s[j] and j-i < 2  
dp[i][j] = max(dp[i+1][j], d[i][j-1] when s[i] != s[j]  
516 - https://leetcode.com/problems/longest-palindromic-subsequence/

Smallest insert steps to make Palindrome:  
a. use insert action  
b. calculate Longest Palindrom subsequence of s, and ans = len(s) - LPS  
1312 - https://leetcode.com/problems/minimum-insertion-steps-to-make-a-string-palindrome/

## 13. Graph + dp

dp[i][j] = at ith step, ending at j node, minimum cost. And to reconstruct the path, we need another parents array, everytime we find a better path for dp[i][v], we update the parents[i][v]  
1548 - https://leetcode.com/problems/the-most-similar-path-in-a-graph/

## 14. To check length of positive product, need to maintain positive[i] and negative[i] dp array, because previouly negative length could become positive length later

1567 - https://leetcode.com/problems/maximum-length-of-subarray-with-positive-product/

## 15. when doing top down DP for string insert/delete/replace

use dp(index, numOfStr) where index is the current index at originial string, numOfStr is the string length we have processes so far, the reason is because when is the insert case, index will stay the same but numOfStr will increase, just like we processed the new inserted char this time, which means the next dp call will still process index letter from the original string  
420 - https://leetcode.com/problems/strong-password-checker/

## 16. how to handle 0 and negative product when getting the biggest product from a list

a. compare with current number to handle previous product result is 0  
b. besides max_product, also maintaining min_product for each position, so that later on we might need to multiple with the min_product to handle the negative product case  
152 - https://leetcode.com/problems/maximum-product-subarray/

a. maintain max and min value from prevous state (in this case it's equivalent to two list which means two sets of max and min values)  
b. and since we will product all the element from the path, no need to handle 0 num case (comparing with the num itself)  
1594 - https://leetcode.com/problems/maximum-non-negative-product-in-a-matrix/


## 17. count submatrices with all ones

square submatrices, if matrix[i-1][j-1] == 1 then dp[i][j] = min(dp[i-1][j], dp[i][j-1], dp[i-1][j-1]) + 1, ans += dp[i][j]  
1277 - https://leetcode.com/problems/count-square-submatrices-with-all-ones/

## 18. use pre_sum to improve DP speed when you need to do ans += dp(i, fixed_num) where i is from start to n

1621 - https://leetcode.com/problems/number-of-sets-of-k-non-overlapping-line-segments/

## 19. one pattern of DP is dp[i] = max(dp[i], dp[j] + current_value) where j is between 0 and i-1, and also needs to check if value[i] and value[j] satisfied the condition.

the most classic example is "longest increasing subsequence", all the numbers that dp[j] represents are increasing. And since there is only one condition and we can not change the ordering of the array, we don't need to do any sorting  
300 - https://leetcode.com/problems/longest-increasing-subsequence/

To restore the sequence maintain a p[] array for the parent, and then restore it in the end
```python
dp = [1] * n
p = [-1] * n

for i in range(1,n):
  for j in range(i)
    if nums[i] > nums[j]:
      if dp[j] + 1 > dp[i]:
        dp[i] = dp[j] + 1
        p[i] = j

# find LIS ending pos
cur = -sys.maxsize
pos = 0
for i ,val in enumerate(dp):
  if val > cur:
    pos = i
    cur = val

ans = []

while pos != -1:
  ans.append(nums[pos])
  pos = p[pos]

return ans[::-1]
```

nlogn solution
```python
dp = []

for num in nums:
  # maintain an increasing array, and the dp length will be the answer
  index = bisect.bisect_left(dp, num)
  
  if index < len(dp):
    # replace the bigger number with the smaller number
    dp[index] = num
  else:
    # if new number is greater than all the numbers, append (length will plus 1)
    dp.append(num)

return len(dp)
```

this example is a bit more complicated, since we need to satisfy two contidions, we cannot simply apply the above template because when condition between item[i] and item[j] are met we will be using dp[j] to calculate current dp[i], but we can't gaurentee two conditions are met for all the items dp[j] stands for. So we have to sort the array first  
1626 - https://leetcode.com/problems/best-team-with-no-conflicts/

## 20. when top down is much faster than bottom up

in bottom up for each state we need to try all possible previous states, while for top down at each state we only need to consider either move left or right finger  
1320 - https://leetcode.com/problems/minimum-distance-to-type-a-word-using-two-fingers/

## 21. Kadane - get max subarray sum

dp with space compression
```python
ans = -sys.maxsize
cur_max = 0

for num in nums:
  cur_max = max(num, cur_max+num)
  ans = max(ans, cur_max)
  
return ans
```

53 - https://leetcode.com/problems/maximum-subarray/submissions/

## 22. use binary search from n^2 to nlogn

LIS - use binary search to maintain a sorted list, and the length of list is the answer  
300 - https://leetcode.com/problems/longest-increasing-subsequence/

max sum of subarray not greater than k, maitain sorted presum and use binary search to find first previous presum list for the current presum
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
363 - https://leetcode.com/problems/max-sum-of-rectangle-no-larger-than-k/

## 23. number of subarrays with sum K
```python
dp = defaultdict(int)
dp[0] = 1 # set 0 with 1 for the first subarray who starts at the beginning
ans = 0
running_sum = 0
for num in nums:
  runnning_sum += num
  target = running_sum - K
  
  if target in dp:
    ans += dp[target]
  
  dp[running_sum] += 1

return ans
```

1074 - https://leetcode.com/problems/number-of-submatrices-that-sum-to-target/

## 24. maintain state trick

1. how to maintain left and up element in a 2D (m x n) grid when filling in from top-down and left-right, use tuple([""] * n) to represent the lastNValues, for new cell with (i, j), left = lastNValues[j-1], up = lastNValues[j]  
1659 - https://leetcode.com/problems/maximize-grid-happiness/

2. when filling in the squares from bottom right corner, use [0] * n to represent the current filled skyLine, and fill in the squares with the smallest hight  
1240 - https://leetcode.com/problems/tiling-a-rectangle-with-the-fewest-squares/

## 25. digit DP:

loop from the end, and if current digit is the same as target digit then dp[i] += dp[i+1], if smaller than the target digit then dp[i] += candidates ** (n-i-1)  
902 - https://leetcode.com/problems/numbers-at-most-n-given-digit-set/

## 26. tree DP:

for node u, and for each child v, from 0 to k ans += dp[u][j] * dp[v][k-j-1] (dp[u][j] means nodes has distance j to u not including the nodes in current child node v, and dp[v][k-j-1] means the nodes count to v whose distance is k-j-1, and the total combination is the mutiply, and after this, update dp[u] with the current child v, so that it can be used for next child node  
https://codeforces.com/problemset/problem/161/D

## 27. when dp[i][j] means from i to j, and in state transition function there is dp[i+1][j] (comparing with palindrome's dp[i+1][j-1], becauuse j-1 has already been processed, so it's ok, but in this case dp[i+1][j] is not processed), and needs to loop length first then loop start index

1690 - https://leetcode.com/problems/stone-game-vii/
