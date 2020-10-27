## 1. how to find start node of cycle

a. use hash table to record seen node, if has seen the node before then, this is the start  
b. first use slow fast pointer to check if they can meet, if yes then has cycle, if no return None. then start from head and the meet point again to loop one more time with one step at a time for both. and the next meet point is the answer  
142 - https://leetcode.com/problems/linked-list-cycle-ii/
