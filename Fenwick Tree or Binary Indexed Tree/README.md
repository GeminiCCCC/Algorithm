**1. Use Fenwick Tree to quickly update and get the pre_sum values, since normal way updating the pre_sum will take O(n) time, and with Fenwick Tree only takes O(logn). 
Problem 315 uses Fenwick Tree to maintain the smaller number for each number so far (traverse from end to start), and every time we have new number being added to the front, we just need to find all the numbers which are smaller than it and sum all the smaller numbers and its smallerCount.
With Fenwick Tree we improve the time complexity from O(n^2) brutal force to O(nlogn) i.e loop through each number o(n) and for each number, search the Tree (logn)**

315 - https://leetcode.com/problems/count-of-smaller-numbers-after-self/
