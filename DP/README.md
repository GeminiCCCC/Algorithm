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
