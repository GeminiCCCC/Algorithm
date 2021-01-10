## 1. 2D matrix word search, need to use backTrack to remove visited node because other branches may need to use the letter for their search

79 - https://leetcode.com/problems/word-search/

## 2. when using backTracking to do in-place update, once we find the answer we don't want to backTrack. So we can create a flag and only backtrack when flag is false.

37 - https://leetcode.com/problems/sudoku-solver/

## 3. how to cut branches

a. if there are multiple elements has the same value, only try one of them  
b. if the current value has exceeded the global best answer, no need to continue  
1723 - https://leetcode.com/problems/find-minimum-time-to-finish-all-jobs/
