**1. min-max problem**

How can you tell it's a min_max problem? 

1) Two players. 
2) Take turns 
3) Both play optimally

Use max relative score (max winning score) to solve it, and traverse from end. And the reason we can traverse from the end is becasue there are constant k ways of taking stones for each player (1460). If the k is changing based on the previous player, then we can do bottom up DP, we have to use top down recursive dp. (1140)

And once we get the final answer for the most scores player A can win against player B,  dp(0) in this case, we can calculate the actual score for A and B,  A = (total + max_winning_against_B) // 2,   B = total - A

1460 - https://leetcode.com/problems/stone-game-iii/

1140 - https://leetcode.com/problems/stone-game-ii/

**2. dp + graph (edges are the possible scenarios at current state)**

568 - https://leetcode.com/problems/maximum-vacation-days/
