```python
def findPattern(s, p):
  n = len(s)
  m = len(p)
  lps = [0] * m
  
  # build lps (longest prefix as suffix)
  j = 0
  for i in range(1, m):
    while j > 0 and p[i] != p[j]:
      j = lps[j-1]
    
    if p[i] == p[j]:
      lps[i] = j+1
      j += 1
  
  # match pattern
  j = 0
  for i in range(n):
    while j > 0 and s[i] != p[j]:
      j = lps[j-1]
    
    # this if check is for when j == 0
    if s[i] == p[j]:
      j += 1
    
    if j == m:
      return True
  
  return False
  
```

1392 - https://leetcode.com/problems/longest-happy-prefix/  
1397 - https://leetcode.com/problems/find-all-good-strings/
