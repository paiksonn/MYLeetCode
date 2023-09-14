- __EASY__ Find the Difference of Two Arrays [link](https://leetcode.com/problems/find-the-difference-of-two-arrays/editorial/?envType=study-plan-v2&envId=leetcode-75)
```python
class Solution:
    def findDifference(self, nums1: List[int], nums2: List[int]) -> List[List[int]]:
        s2 = set(nums2)
        s1 = set(nums1)
        return [list(s1-s2),list(s2-s1)]
```

- __EASY__ Unique Number of Occurrences [link](https://leetcode.com/problems/unique-number-of-occurrences/description/?envType=study-plan-v2&envId=leetcode-75)
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

