**1. to get combinations of length k**

a. use backTrack with current index and current length as parameters to pre-calculate all combinations

b. if need to get next combination, need to use index_map and find the first letter that can be moved to the next

1286 - https://leetcode.com/problems/iterator-for-combination/

**2. when check the substring include all appearance of a letter, preprocess the last index for each letter**

763 - https://leetcode.com/problems/partition-labels/
