# Greedy:

**1520. https://leetcode.com/problems/maximum-number-of-non-overlapping-substrings/**

Need to get all the valid substrings first, and then the problem becomes the schedule meeting problem, where you have one meeting room, what's the most meeting numbers you can schedule


Others:

659 - https://leetcode.com/problems/split-array-into-consecutive-subsequences/

1057 - https://leetcode.com/problems/campus-bikes/

678 - https://leetcode.com/problems/valid-parenthesis-string/solution/

527 - https://leetcode.com/problems/word-abbreviation/

## 1. use greedy idea to fill in the idle space to calculate min CPU time, first we get the total minimum idle space with most refrequent task, and then greedily fill in the idle space with the remaining tasks

621 - https://leetcode.com/problems/task-scheduler/

## 2. use greedy idea to find the smallest permutation from 1 to n based on 'D' or 'I'**

use stack to keep track of how many consecutive Ds we have seen so far, and reverse the numbers when we see an 'I'

484 - https://leetcode.com/problems/find-permutation/

## 3. interval problems

a. ususally use greedy idea to solve it.

b. sort by end time: use the interval ending earliest will give us more room to fill rest intervals.

435 - https://leetcode.com/problems/non-overlapping-intervals/

## 4. use greedy + pq inside hash table to solve problem

use hash table: key is the ending number, value is the pq of the lengths who is ending with the key, for each num find the pq ending list, and then get the smallest length  
659 - https://leetcode.com/problems/split-array-into-consecutive-subsequences/

## 5. lazy greedy - go with one scenario until it can't go anymore, then among all the previously steps find the min/max (usually max) value to replace with another option so that you can continue going forward

871 - https://leetcode.com/problems/minimum-number-of-refueling-stops/  
1642 - https://leetcode.com/problems/furthest-building-you-can-reach/  
45 - https://leetcode.com/problems/jump-game-ii/
