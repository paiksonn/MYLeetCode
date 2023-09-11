- __EASY__ Move Zeroes [link](https://leetcode.com/problems/move-zeroes/?envType=study-plan-v2&envId=leetcode-75)
```python
# Brutforce solution

class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        for num in nums:
            if num == 0:
                nums.append(num)
                nums.remove(0)

# Solution sing two-pointers

class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        left = 0
        for right in range(len(nums)):
            if nums[right] != 0 and nums[left] == 0:
                nums[left], nums[right] = nums[right], nums[left]

            # wait while we find a non-zero element to
            # swap with you
            if nums[left] != 0:
                left += 1
```

