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

**3. For problem that has two moving points, then need to have three/four dimension dp, and for the problem start from one point and the stop point is not fixed, then top down DP is better**

741 - https://leetcode.com/problems/cherry-pickup/ # for cherry pick problems: 1. when two people on the same cell, only collect cherry once. 2 use -sys.maxsize to indicate invalid path

1463 - https://leetcode.com/problems/cherry-pickup-ii/

1320 - https://leetcode.com/problems/minimum-distance-to-type-a-word-using-two-fingers/
