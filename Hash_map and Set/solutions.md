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

- #657 Robot Return to Origin [link](https://leetcode.com/problems/robot-return-to-origin/description/)
```python
class Solution:
    def judgeCircle(self, moves: str) -> bool:
        lib = {'R':0, 'L':0, 'U':0, 'D':0}
        for move in moves:
            lib[move] += 1

        return (lib['R'] - lib['L'] == 0) & (lib['U'] - lib['D'] == 0)

```


- #387 First Unique Character in a String [link](https://leetcode.com/problems/first-unique-character-in-a-string/description/)
```python
from collections import Counter 

class Solution:
    def firstUniqChar(self, s: str) -> int:
        counted_dict = Counter(s)
        for idx in range(len(s)):
            if counted_dict[s[idx]] == 1:
                return idx
                
        return -1  
```


- #415 Add Strings [link](https://leetcode.com/problems/add-strings/description/)
```python
class Solution:
    def addStrings(self, num1: str, num2: str) -> str:
                
        # with dict
         def str2int(num):
            numDict = {'0' : 0, '1' : 1, '2' : 2, '3' : 3, '4' : 4, '5' : 5,
                  '6' : 6, '7' : 7, '8' : 8, '9' : 9}
            output = 0
            for d in num:
                output = output * 10 + numDict[d]
            return output
        
        return str(str2int(num1) + str2int(num2)) 

        # with unicode
        def str2int(num):
            result  = 0
            for n in num:
                result = result * 10 + ord(n) - ord('0')
            return result
        return str(str2int(num1) + str2int(num2))
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

