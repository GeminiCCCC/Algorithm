**1. To check if the word is a subsequence of S, instead of scanning the S one by one, we can use binary search**

So the idea is to maintain a hashMap for each letter and its indices, and we also maintain the pre_pos, the goal is to find for current letter c, can we find an index for this c who is greater than the pre_pos. If we can't, then it's not a subsequence

792 - https://leetcode.com/problems/number-of-matching-subsequences/
