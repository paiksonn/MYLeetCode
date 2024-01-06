__EASY__ 

- #374 Guess Number Higher or Lower [link](https://leetcode.com/problems/guess-number-higher-or-lower/?envType=study-plan-v2&envId=leetcode-75)
```python
class Solution:
    def guessNumber(self, n: int) -> int:
        down, up = 0, n
        while down <= up:
            mid = (down + up) // 2
            res = guess(mid)
            if res < 0:
                up = mid - 1
            elif res > 0:
                down = mid + 1
            else:
                return mid

```

__MEDIUM__ 

- #2300 Successful Pairs of Spells and Potions [link](https://leetcode.com/problems/successful-pairs-of-spells-and-potions/?envType=study-plan-v2&envId=leetcode-75)
```python
class Solution:
    def successfulPairs(self, spells: List[int], potions: List[int], success: int) -> List[int]:
        potions.sort()
        ans = []
        for spell in spells:
            l, r = 0, len(potions) - 1
            k = success / spell
            while l <= r:
                mid = (l + r) // 2
                if potions[mid] >= k:
                    r = mid - 1
                else:
                    l = mid + 1
            ans.append(len(potions) - l)

        return ans
```

- #162 Find Peak Element [link](https://leetcode.com/problems/find-peak-element/?envType=study-plan-v2&envId=leetcode-75)
```python
class Solution:
    def findPeakElement(self, nums: List[int]) -> int:
        left = 0
        right = len(nums) - 1
        while(left < right):
            mid = left +(right-left+1) // 2 
            if nums[mid] < nums[mid-1]: 
                right = mid - 1
            else:
                left = mid
        return left
```

