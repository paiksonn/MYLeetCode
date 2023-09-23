- __EASY__ N-th Tribonacci Number [link](https://leetcode.com/problems/n-th-tribonacci-number/?envType=study-plan-v2&envId=leetcode-75)
```python
from collections import defaultdict

class Solution:
    def tribonacci(self, n: int) -> int:
        memo = defaultdict(int)
        memo[0], memo[1], memo[2] = 0, 1, 1
        for i in range(3,n+1):
            memo[i] = memo[i-1] + memo[i-2] + memo[i-3]
        return memo[n]
```

- __EASY__ Min Cost Climbing Stairs [link](https://leetcode.com/problems/min-cost-climbing-stairs/?envType=study-plan-v2&envId=leetcode-75)
```python
class Solution:
     def minCostClimbingStairs(self, cost: List[int]) -> int:
        if not cost:
            return 0
        n = len(cost)
        dp = [0] * n
        dp[0] = cost[0]
        if n >= 2:
            dp[1] = cost[1]
        for i in range (2, n):
            dp[i] = cost[i] + min(dp[i-1], dp[i-2])
        return min(dp[-1], dp[-2])
```

