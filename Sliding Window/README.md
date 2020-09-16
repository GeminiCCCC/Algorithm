**1. The nature of sliding window is that every time we move the end pointer to the next position, first we will update the start pointer if necessary, second with the new end pointer, we can get either min or max value with all the other elements before end pointer, by maintaining the min/max value for the current sliding window by using heap or monotonic queue**

1499 - https://leetcode.com/problems/max-value-of-equation/
