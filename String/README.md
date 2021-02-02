## 1. to get combinations of length k

a. use backTrack with current index and current length as parameters to pre-calculate all combinations

b. if need to get next combination, need to use index_map and find the first letter that can be moved to the next

1286 - https://leetcode.com/problems/iterator-for-combination/

## 2. when check the substring include all appearance of a letter, preprocess the last index for each letter

763 - https://leetcode.com/problems/partition-labels/

## 3. convert s to t

a. same length and sort sub string, instead sorting we should think this problem by trying to move the cur char of t to the beginning the updated s (if there is no smaller number before cur char in s)  
1585 - https://leetcode.com/problems/check-if-string-is-transformable-with-substring-sort-operations/
