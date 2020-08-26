**1. Merge range length**

get left_length = lengths[num-1] and right_length = lengths[num+1], new length is left + right + 1, and only needs to update lengths[num-left] = lengths[num+right] = new_length

128 - https://leetcode.com/problems/longest-consecutive-sequence/  
1562 - https://leetcode.com/problems/find-latest-group-of-size-m/
