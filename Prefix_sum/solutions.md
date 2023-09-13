- __EASY__ Find the Highest Altitude [link](https://leetcode.com/problems/find-the-highest-altitude/?envType=study-plan-v2&envId=leetcode-75)
```python
class Solution:
    def largestAltitude(self, gain: List[int]) -> int:
        summ = 0
        max_sum = 0
        for el in gain:
            summ += el
            if max_sum < summ:
                max_sum = summ
        return max_sum
```

- __EASY__ Find Pivot Index [link](https://leetcode.com/problems/find-pivot-index/?envType=study-plan-v2&envId=leetcode-75)
```python
class Solution:
    def pivotIndex(self, nums: List[int]) -> int:
        left_sum = right_sum = 0
        for i in range(len(nums)):
            left_sum = sum(nums[:i])
            right_sum = sum(nums[i+1:])
            if left_sum == right_sum:
                return i
        return -1
```

