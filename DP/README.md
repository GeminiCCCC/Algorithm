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

416 - https://leetcode.com/problems/partition-equal-subset-sum/

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
