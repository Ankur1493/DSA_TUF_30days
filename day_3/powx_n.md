# Pow(x,n)

## Brute Force

1) keep multiplying by using a loop till i reaches n

**Time Complexity** o(n)

## Optimal

**NOTE- this works when n is positive, if n will be negative we will have to make sure of some edge cases**

1) if we are given to calculate 2^10 we can say it's equal to (2*2)^5 
2) now it's equal to 4^5 
3) now 4^5 = 4 * (4)^4 
4) and similarly as step 1 it's equal to 4 * (4*4)^2 
5) 16^2  = 4 * (16*16)

**CODE**

```cpp
class Solution {
public:
double myPow(double x, int n) {
  double ans = 1.0;
  long long nn = n;
  if (nn < 0) nn = -1 * nn;
  while (nn) {
    if (nn % 2) {
      ans = ans * x;
      nn = nn - 1;
    } else {
      x = x * x;
      nn = nn / 2;
    }
  }
  if (n < 0) ans = (double)(1.0) / (double)(ans);
  return ans;
}
};
```
**time complexity** O(log2n)

