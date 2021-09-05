## 1. Calculate combination (within left and right set, the relative position cannot be changed)

a. (left+right)! // left! // right!, we can precalculate all factorials from 1 to (left+right)  
1569 - https://leetcode.com/problems/number-of-ways-to-reorder-array-to-get-same-bst/

## 2. use combination to check remaining possible string combination

1643 - https://leetcode.com/problems/kth-smallest-instructions/

## 3. calculate sum from n to n-k

```python
start = n
end = n - k - 1
start * (start+1) // 2 - end * (end+1) // 2
```

1648 - https://leetcode.com/problems/sell-diminishing-valued-colored-balls/

## 4. gcd

```python
def gcd(a, b):
  # Unless b == 0, the result will have the same sign as b
  while b:
    a, b = b, a % b
  
  return a  
```

## 5. ceiling issue with float

If ceiling with sum of some floats, we may end up getting n+1 instead of n, the fix is to subtrac a esplon value like 1e-9 every time before ceiling  
1883 - https://leetcode.com/problems/minimum-skips-to-arrive-at-meeting-on-time/

## 6. check if a number is perfect square number

```c++
double root = sqrt(num)

if (root == ceil(root))
{
  return true;
}
else
{
  return false;
}
```

or 

```c++
for (int i=1;i*i<=num;i++)
{
  if (i*i == num)
  {
    return true;
  }
}

return false;
```

## 7. check is a number is prime number

```c++
if (num == 1)
{
  return false;
}

for (int i=2; i*i<=num; i++)
{
  if (num % i == 0)
  {
    return false;
  }
}

return true;
```

## 8. get all prime numbers within n - Sieve of Eratosthenes

```c++
vector<bool> prime(n+1, true);

for (int p=2;p*p<=n;p++)
{
  if (prime[p])
  {
    for (int i=p*p;i<=n;i+=p)
    {
      prime[i] = false;
    }
  }
}
```

