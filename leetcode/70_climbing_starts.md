# 70. Climbing Stairs

at each stair level, the number of ways to climb the stairs is the number of ways of N - 1 and N - 2. This is fib
The trick is to use a decision tree to visualize the problem. you can memoize the same trees in the brute force solution
Time complexity: O(N)
Space complexity: O(N)

CAN USE CONSTANT MEMORY

```python
class Solution:
    # This is O(N) space
    # However, we only look at the last two vars ever
    def climbStairs(self, n: int) -> int:
        if n == 1:
            return 1
        dp = [0] * n
        dp[-1] = 1
        dp[-2] = 2
        for i in reversed(range(n-2)):
            dp[i] = dp[i+1] + dp[i+2]
        return dp[0]

class Solution:
    def climbStairs(self, n: int) -> int:
        one, two = 1, 1
        for i in range(n-1):
            temp = one
            one = one + two
            two = temp
        return one
```


