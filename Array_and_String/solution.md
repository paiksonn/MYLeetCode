- __EASY__ Merge Strings Alternately [link](https://leetcode.com/problems/merge-strings-alternately/description/?envType=study-plan-v2&envId=leetcode-75)
```python
# Fast but memory-heavy
class Solution:
    def mergeAlternately(self, word1: str, word2: str) -> str:
        p1, p2 = 0, 0
        ans = ''
        while p1 < len(word1) and p2 < len(word2):
            ans += word1[p1] + word2[p2] 
            p1 += 1
            p2 += 1
        if p1 < len(word1):
            ans += word1[p1:]
        elif p2 < len(word2):
            ans += word2[p2:]
        return ans

# Slow but memory-light
class Solution:
    def mergeAlternately(self, word1: str, word2: str) -> str:
        return "".join(a + b for a, b in zip(word1, word2)) + word1[len(word2):] + word2[len(word1):]
```

- __EASY__ Greatest Common Divisor of Strings [link](https://leetcode.com/problems/greatest-common-divisor-of-strings/description/?envType=study-plan-v2&envId=leetcode-75)
```python
class Solution:
    def gcdOfStrings(self, str1: str, str2: str) -> str:
        if str1 + str2 != str2 + str1:
            return ''
        # gcd - Greatest Common Diviser
        max_length = gcd(len(str1), len(str2))
        return str1[:max_length]
```

- __EASY__ Kids With the Greatest Number of Candies [link](https://leetcode.com/problems/kids-with-the-greatest-number-of-candies/description/?envType=study-plan-v2&envId=leetcode-75)
```python
class Solution:
    def kidsWithCandies(self, candies: List[int], extraCandies: int) -> List[bool]:
        max_candies = max(candies)
        ans = [] * len(candies)
        for i in range(len(candies)):
            if candies[i] + extraCandies >= max_candies:
                ans.append(True)
            else:
                ans.append(False)
        return ans

# Shorter version
class Solution:
    def kidsWithCandies(self, candies: List[int], extraCandies: int) -> List[bool]:
        diff = max(candies) - extraCandies
        return [candy >= diff for candy in candies]
```

- __EASY__ Can Place Flowers [link](https://leetcode.com/problems/can-place-flowers/description/?envType=study-plan-v2&envId=leetcode-75)
```python
class Solution:
    def canPlaceFlowers(self, flowerbed: List[int], n: int) -> bool:
        for i in range(len(flowerbed)):
            if flowerbed[i] == 0:
                left_pot = (i == 0) or (flowerbed[i-1] == 0)
                right_pot = (i == len(flowerbed) - 1) or (flowerbed[i+1] == 0)
                if left_pot and right_pot:
                    flowerbed[i] = 1
                    n -= 1
                    if n <= 0:
                        return True
        return n <= 0
```

- __EASY__ Reverse Vowels of a String [link](https://leetcode.com/problems/reverse-vowels-of-a-string/description/?envType=study-plan-v2&envId=leetcode-75)
```python
class Solution:
    def reverseVowels(self, s: str) -> str:
        s = list(s)
        n = len(s)
        l, r = 0, n-1
        letters = ['a', 'e', 'i', 'o', 'u', 'A', 'E', 'I', 'O', 'U']
        while l < r:
            if s[l] in letters and s[r] in letters:
                s[l], s[r] = s[r], s[l]
                l += 1
                r -= 1
            elif s[r] not in letters:
                r -= 1
            elif s[l] not in letters:
                l += 1
        return ''.join(s)
```

- __MEDIUM__ Reverse Words in a String [link](https://leetcode.com/problems/reverse-words-in-a-string/description/?envType=study-plan-v2&envId=leetcode-75)
```python
class Solution:
    def reverseWords(self, s: str) -> str:
        return ' '.join(s.split()[::-1])
```

- __MEDIUM__ Product of Array Except Self [link](https://leetcode.com/problems/product-of-array-except-self/description/?envType=study-plan-v2&envId=leetcode-75)
 ```python
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        n = len(nums)
        ans = [1] * n
        prefix = 1
        postfix = 1
        for i in range(n):
            ans[i] *= prefix
            prefix = prefix * nums[i]
            ans[n-i-1] *= postfix
            postfix = postfix * nums[n-i-1]
        return(ans)
```

- __MEDIUM__ Increasing Triplet Subsequence [link](https://leetcode.com/problems/increasing-triplet-subsequence/description/?envType=study-plan-v2&envId=leetcode-75)
```python
class Solution:
    def increasingTriplet(self, nums: List[int]) -> bool:
        first, second = inf, inf
        for third in nums:
            if second < third: return True
            if third <= first: first= third    
            else:  second = third 
                
        return  False
```

- __MEDIUM__ String Compression [link](https://leetcode.com/problems/string-compression/description/?envType=study-plan-v2&envId=leetcode-75)
```python
class Solution:
  def compress(self, chars: List[str]) -> int:
    ans = 0
    i = 0

    while i < len(chars):
      letter = chars[i]
      count = 0
      while i < len(chars) and chars[i] == letter:
        count += 1
        i += 1
      chars[ans] = letter
      ans += 1
      if count > 1:
        for c in str(count):
          chars[ans] = c
          ans += 1

    return ans
```
- __MEDIUM__ 3Sum [link](https://leetcode.com/problems/3sum/)
```python
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        nums.sort()
        triplets = set()
        for i in range(len(nums) - 2):
            if i > 0 and nums[i] == nums[i - 1]:
                continue
            j = i + 1
            k = len(nums) - 1
            while j < k:
                sum = nums[i] + nums[j] + nums[k]
                if sum > 0:
                    k -= 1
                elif sum < 0:
                    j += 1
                else:
                    triplets.add((nums[i], nums[j], nums[k]))
                    j += 1
                    k -= 1
        return triplets
```

- __MEDIUM__ 3Sum Closest [link](https://leetcode.com/problems/3sum-closest/description/)
```python
class Solution:
    def threeSumClosest(self, nums: List[int], target: int) -> int:
        nums.sort()
        closest = 1e9
        for i in range(len(nums) - 2):
            j = i + 1
            k = len(nums) - 1
            while j < k:
                sum = nums[i] + nums[j] + nums[k]
                if sum < target:
                    j += 1
                else:
                    k -= 1
                if abs(sum - target) < abs(closest - target):
                    closest = sum
        return closest
```

