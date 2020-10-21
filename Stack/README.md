## 1. solve problems with nested brackets

logic is every time sees left bracket, append a list or hashmap to the stack. every time sees right bracket, cur = stack.pop(). Then find the multiplier after right bracket. Then for loop each item in cur and calculate with multiplier. Then add the result back to stack[-1]. In the end the list/hashTable remain in the stack is the result.

726 - https://leetcode.com/problems/number-of-atoms/  
1087 - https://leetcode.com/problems/brace-expansion/  //assuming we have nested brace

