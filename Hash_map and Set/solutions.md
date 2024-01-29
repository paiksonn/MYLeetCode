__EASY__ 

- #1 Two Sum [link](https://leetcode.com/problems/two-sum/description/)
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        numMap = {}
        n = len(nums)

        # Build the hash table
        for i in range(n):
            numMap[nums[i]] = i

        # Find the complement
        for i in range(n):
            complement = target - nums[i]
            if complement in numMap and numMap[complement] != i:
                return [i, numMap[complement]]
```

-  #2215 Find the Difference of Two Arrays [link](https://leetcode.com/problems/find-the-difference-of-two-arrays/editorial/?envType=study-plan-v2&envId=leetcode-75)
```python
class Solution:
    def findDifference(self, nums1: List[int], nums2: List[int]) -> List[List[int]]:
        s2 = set(nums2)
        s1 = set(nums1)
        return [list(s1-s2),list(s2-s1)]
```

- #1207 Unique Number of Occurrences [link](https://leetcode.com/problems/unique-number-of-occurrences/description/?envType=study-plan-v2&envId=leetcode-75)
```python
class Solution:
    def uniqueOccurrences(self, arr: List[int]) -> bool:
        dic = {}
        # create a hash map
        for i in arr:
            if i in dic:
                dic[i] += 1
            else:
                dic[i] = 1
        
        if len(set(dic.values())) != len(set(arr)):
            return False
        return True
```

- #169 Majority Element [link](https://leetcode.com/problems/majority-element/description/)
```python
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        threshhlod = len(nums) // 2
        numbers = {}

        for i in nums:
            if i in numbers:
                numbers[i] += 1
            else:
                numbers[i] = 1
        
        max_el = 0
        ans = 0
        for key, value in numbers.items():
            if value > max_el:
                max_el = value
                ans = key
        
        return ans
```


__MEDIUM__
  
- #1657 Determine if Two Strings Are Close [link](https://leetcode.com/problems/determine-if-two-strings-are-close/description/?envType=study-plan-v2&envId=leetcode-75)
```python
from collections import Counter

class Solution:
    def closeStrings(self, word1: str, word2: str) -> bool:
        c1, c2 = Counter(word1), Counter(word2)
        return c1.keys() == c2.keys() and sorted(c1.values()) == sorted(c2.values())
```

- #2352 Equal Row and Column Pairs [link](https://leetcode.com/problems/equal-row-and-column-pairs/?envType=study-plan-v2&envId=leetcode-75)
```python
class Solution:
    def equalPairs(self, grid: List[List[int]]) -> int:
        freq = Counter(tuple(row) for row in grid)
        # zip(*grid) gives as a transpose matrix
        return sum(freq[tuple(col)] for col in zip(*grid))
```

