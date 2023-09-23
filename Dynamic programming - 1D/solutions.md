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
        def dp(n):  
            # write down base cases
            if n < 2: 
                return cost[n] 
            # write recursive function based on what you can change (climb one or two steps)
            return cost[n] + min(dp(n-1), dp(n-2))
		
		# since we want to know the min cost to get to the final step, we use the code below 
        length = len(cost) 
        return min(dp(length-1), dp(length-2))
```

