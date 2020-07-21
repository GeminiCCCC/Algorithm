**template:**

```
# don't forget to initialize each component's parent to its self
parents = [0,......n-1]
ranks = [0]*n

def find(x):
  # path compression
  if parents[x] != x:
    parents[x] = find(parents[x])

  return parents[x]

def union(x, y):
  r1 = find(x)
  r2 = find(y) 

  # if root are the same, already unioned before, no need to continue
  if r1 != r2:
    # always assign the lower rank to higher rank
    if ranks[r1] > ranks[r2]:
      parents[r2] = r1
    elif ranks[r1] < ranks[r2]:
      parents[r1] = r2
    else:
      # if ranks are the same, assign either one is ok
      parents[r2] = r1
      ranks[r1] += 1

```

**1. to find if a graph has cycle**
```
def hasCycle(edges):
  # build the graph from edges, if we are looping all the neighbors here, we will only create one edge for we can simply loop through the edges
  #graph = defaultdict(list)

  for u, v in edges:
    r1 = find(u)
    r2 = find(v)
    # this is because before union the new node, the root of the new node will always be itself, and we are doing the dfs here, if there is a cycle, by the time we see the neighbor second time, the neighbor would already had been unioned, which will give us r1 == r2
    if r1 == r2:
      # has cycle
      return True
    else:
      # or we can make union return True/False and save the if check here
      union(r1, r2)

  return False
```

**2. use size for the component to solve problem**

803. https://leetcode.com/problems/bricks-falling-when-hit/
