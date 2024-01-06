__EASY__ 

- #1732 Find the Highest Altitude [link](https://leetcode.com/problems/find-the-highest-altitude/?envType=study-plan-v2&envId=leetcode-75)
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

- #724 Find Pivot Index [link](https://leetcode.com/problems/find-pivot-index/?envType=study-plan-v2&envId=leetcode-75)
```python
# REALLY slow decision but i did it myself ^^

class Solution:
    def pivotIndex(self, nums: List[int]) -> int:
        left_sum = right_sum = 0
        for i in range(len(nums)):
            left_sum = sum(nums[:i])
            right_sum = sum(nums[i+1:])
            if left_sum == right_sum:
                return i
        return -1

# optimized code

# Time Complexity : O(n)
# Space Complexity : O(1)
class Solution(object):
    def pivotIndex(self, nums):
        # Initialize leftSum & rightSum to store the sum of all the numbers strictly to the index's left & right respectively...
        leftSum, rightSum = 0, sum(nums)
        # Traverse elements through the loop...
        for idx, ele in enumerate(nums):
            rightSum -= ele
            # If the sum of all the numbers strictly to the left of the index is equal to the sum of all the numbers strictly to the index's right...
            if leftSum == rightSum:
                return idx      # Return the pivot index...
            leftSum += ele
        return -1       # If there is no index that satisfies the conditions in the problem statement...
```

