## 1. The nature of sliding window is that every time we move the end pointer to the next position, first we will update the start pointer if necessary, second with the new end pointer, we can get either min or max value with all the other elements before end pointer, by maintaining the min/max value for the current sliding window by using heap or monotonic queue

1499 - https://leetcode.com/problems/max-value-of-equation/

## 2. When counting total sub arrays using sliding windows, loop right pointer(do not loop left pointer) and then update the sliding window, because the right pointer tells us how many more new sub arrays we will get by adding the right pointer num

when loop left pointer does not work, try to loop right pointer  
713 - https://leetcode.com/problems/subarray-product-less-than-k/

## 3. when asking to remove from leftmost or rightmost, transform it to get the answer for the remaining subarray which is a sliding window problem  

1423 - https://leetcode.com/problems/maximum-points-you-can-obtain-from-cards/  
1658 - https://leetcode.com/problems/minimum-operations-to-reduce-x-to-zero/

## 4. at least k problems. loop right pointer first, and then try to shink left pointer when the condition is satisified. And every time after shrinking the left pointer add n - r to the ans

1358 - https://leetcode.com/problems/number-of-substrings-containing-all-three-characters/

## 5. use at least k to solve exact k, exact k = atleast k - atleast k +- 1 (depending on which condition is looser)

3306 - https://leetcode.com/problems/count-of-substrings-containing-every-vowel-and-k-consonants-ii
