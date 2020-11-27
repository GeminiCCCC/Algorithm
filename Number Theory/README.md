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
