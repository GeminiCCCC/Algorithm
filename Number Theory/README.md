## 1. check if a number is perfect square number

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

## 2. check is a number is prime number

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

## 3. get all prime numbers within n - Sieve of Eratosthenes

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
