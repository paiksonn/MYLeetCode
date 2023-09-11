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

- __EASY__ Is Subsequence [link](https://leetcode.com/problems/is-subsequence/?envType=study-plan-v2&envId=leetcode-75)
```python
# MY solution

class Solution:
    def isSubsequence(self, s: str, t: str) -> bool:
        subseq = list(s)
        seq = list(t)
        i = 0
        if len(subseq) == 0:
            return True
        for c in seq:
            if i < len(subseq) and c == subseq[i]:
                i += 1
        if i == len(subseq):
            return True
        else:
            return False

# Two-pointers solution

class Solution:
    def isSubsequence(self, s: str, t: str) -> bool:
		## TIME COMPLEXITY : O(N) ##
		## SPACE COMPLEXITY : O(1) ##

        p1 = p2 = 0
        while p1 < len(s) and p2 < len(t):
            # move both pointers or just the right pointer
            if s[p1] == t[p2]:
                p1 += 1
            p2 += 1
        return p1 == len(s)
```

- __MEDIUM__ Container With Most Water [link](https://leetcode.com/problems/container-with-most-water/?envType=study-plan-v2&envId=leetcode-75)
```python
class Solution:
    def maxArea(self, height: List[int]) -> int:
        l, r, area = 0, len(height)-1, 0
        while l < r:
            min_height = min(height[l], height[r])
            area = max(area, min_height * (r - l))
            if height[l] < height[r]:
                l += 1
            else:
                r -= 1
        return area
```
