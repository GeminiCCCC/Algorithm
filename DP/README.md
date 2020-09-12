**1. min-max problem**

How can you tell it's a min_max problem? 

1) Two players. 
2) Take turns 
3) Both play optimally

Use max relative score (max winning score) to solve it, and traverse from end. And the reason we can traverse from the end is becasue there are constant k ways of taking stones for each player (1460). If the k is changing based on the previous player, then we can do bottom up DP, we have to use top down recursive dp. (1140)

And once we get the final answer for the most scores player A can win against player B,  dp(0) in this case, we can calculate the actual score for A and B,  A = (total + max_winning_against_B) // 2,   B = total - A

1460 - https://leetcode.com/problems/stone-game-iii/

1140 - https://leetcode.com/problems/stone-game-ii/

**1.1 another kind of min max problem**

375 - https://leetcode.com/problems/guess-number-higher-or-lower-ii/

**2. dp + graph (edges are the possible scenarios at current state)**

568 - https://leetcode.com/problems/maximum-vacation-days/

**3. For problem that has two moving points, then need to have three/four dimension dp, and for the problem start from one point and the stop point is not fixed, then top down DP is better**

741 - https://leetcode.com/problems/cherry-pickup/ # for cherry pick problems: 1. when two people on the same cell, only collect cherry once. 2 use -sys.maxsize to indicate invalid path

1463 - https://leetcode.com/problems/cherry-pickup-ii/

1320 - https://leetcode.com/problems/minimum-distance-to-type-a-word-using-two-fingers/

**4. String DP problems**

4.1 singe string: with in a range, split the range into all possible two sub strings, and calculate the first substring result(find a way to calculate the optimal result) and use dp to calculate the rest substring

1531 - https://leetcode.com/problems/string-compression-ii/

**5. DP to calculate all possible ways with 2D pre sum, 2D pre sum is the way to get counts with in a sub 2D matrix**

1444 - https://leetcode.com/problems/number-of-ways-of-cutting-a-pizza/

**6. Buy and Sell Stock problems, always use buy[i] and sell[i] to store: by index i and last transaction was buy/sell, what's the max profit. And the answer is sell[n-1]**

309 - https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/

if you only allow to do k transactions, then need to have 2nd dimension for buy and sell dp array, buy[i][k] = for the first ith prices, last action was buy and with at most k transactions. And notice that to calculate sell[i][k], we should use buy[i-1][k], not buy[i-1][k-1] becasue buy stock/sell stock is considered as one transaction.

123 - https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/


**7. knapsack**

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

**8. Bit trick + DP**

To union two sets of items, we can convert each set to its binary format and do | for two sets

1125 - https://leetcode.com/problems/smallest-sufficient-team/

**9. Current color/number cannot be the same as preivous one( or can only has k consecutive times)**

for k consecutive times, we will need to add another dimension for k. And when k = 1 this is the special case, it means that we can get to k=1 from all previous state as long as the current number is not the same as previous number

1223 - https://leetcode.com/problems/dice-roll-simulation/

**10. minimum swaps to make two list strictly increasing**

A[i] > A[i-1] and B[i] > B[i-1]  
A[i] > B[i-1] and B[i] > A[i-1]

need to use two dp arrays, swap[i] and not_swap[i], because swap/not_swap will have different impact (similar like stocks problems, sell/not sell)

801 - https://leetcode.com/problems/minimum-swaps-to-make-sequences-increasing/

**11. greedy + dp**

1553 - https://leetcode.com/problems/minimum-number-of-days-to-eat-n-oranges/

**12. Palindrome**

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

**13. Graph + dp**

dp[i][j] = at ith step, ending at j node, minimum cost. And to reconstruct the path, we need another parents array, everytime we find a better path for dp[i][v], we update the parents[i][v]  
1548 - https://leetcode.com/problems/the-most-similar-path-in-a-graph/

**14. To check length of positive product, need to maintain positive[i] and negative[i] dp array, because previouly negative length could become positive length later**

1567 - https://leetcode.com/problems/maximum-length-of-subarray-with-positive-product/

**15. when doing top down DP for string insert/delete/replace**

use dp(index, numOfStr) where index is the current index at originial string, numOfStr is the string length we have processes so far, the reason is because when is the insert case, index will stay the same but numOfStr will increase, just like we processed the new inserted char this time, which means the next dp call will still process index letter from the original string  
420 - https://leetcode.com/problems/strong-password-checker/

**16. how to handle 0 and negative product when getting the biggest product from a list**

a. compare with current number to handle previous product result is 0  
b. besides max_product, also maintaining min_product for each position, so that later on we might need to multiple with the min_product to handle the negative product case  
152 - https://leetcode.com/problems/maximum-product-subarray/

