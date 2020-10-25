## 1. To check if the word is a subsequence of S, instead of scanning the S one by one, we can use binary search

So the idea is to maintain a hashMap for each letter and its indices, and we also maintain the pre_pos, the goal is to find for current letter c, can we find an index for this c who is greater than the pre_pos. If we can't, then it's not a subsequence

792 - https://leetcode.com/problems/number-of-matching-subsequences/

## 2. remember binary search is always seach the answer directly, and with the mid value create the helper function to determine go to left or right, and to get minimum value, right = mid, to get maximum value, left = mid, when using left = mid please use mid = left + (right - left + 1) // 2

1552 - https://leetcode.com/problems/magnetic-force-between-two-balls/  use greedy to calculate the helper function result

## 3. when you see a graph like problem, remember you can also try to use binary search, don't stuck with pure BFS or DFS

1631 - https://leetcode.com/problems/path-with-minimum-effort/
