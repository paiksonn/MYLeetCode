__EASY__ 

- #1768 Merge Strings Alternately [link](https://leetcode.com/problems/merge-strings-alternately/description/?envType=study-plan-v2&envId=leetcode-75)
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

- #1071 Greatest Common Divisor of Strings [link](https://leetcode.com/problems/greatest-common-divisor-of-strings/description/?envType=study-plan-v2&envId=leetcode-75)
```python
class Solution:
    def gcdOfStrings(self, str1: str, str2: str) -> str:
        if str1 + str2 != str2 + str1:
            return ''
        # gcd - Greatest Common Diviser
        max_length = gcd(len(str1), len(str2))
        return str1[:max_length]
```

- #1431 Kids With the Greatest Number of Candies [link](https://leetcode.com/problems/kids-with-the-greatest-number-of-candies/description/?envType=study-plan-v2&envId=leetcode-75)
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

- #605 Can Place Flowers [link](https://leetcode.com/problems/can-place-flowers/description/?envType=study-plan-v2&envId=leetcode-75)
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

- #345 Reverse Vowels of a String [link](https://leetcode.com/problems/reverse-vowels-of-a-string/description/?envType=study-plan-v2&envId=leetcode-75)
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

- #27 Remove Element [link](https://leetcode.com/problems/remove-element/description/)
```python
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        index = 0
        for i in range(len(nums)):
            if nums[i] != val:
                nums[index] = nums[i]
                index += 1
        return index
                
```

- #121 Best Time to Buy and Sell Stock [link](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/)
```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        max_profit = 0
        min_purchase = prices[0]
        for i in range(1, len(prices)):		
            max_profit = max(max_profit, prices[i] - min_purchase)
            min_purchase = min(min_purchase, prices[i])

        return max_profit
```

- #125 Valid Palindrome [link](https://leetcode.com/problems/valid-palindrome/description/)
```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        correct_str = ''.join(item.lower() for item in s if item.isalnum())
        return correct_str == correct_str[::-1]
```


- #205 Isomorphic Strings [link](https://leetcode.com/problems/isomorphic-strings/description/)
```python
class Solution:
    def isIsomorphic(self, s: str, t: str) -> bool:
        map1 = []
        map2 = []

        for idx in s:
            map1.append(s.index(idx))

        for idx in t:
            map2.append(t.index(idx))

        return map1 == map2
```


- #977 Squares of a Sorted Array [link](https://leetcode.com/problems/squares-of-a-sorted-array/description/)
```python
class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        return sorted([num**2 for num in nums])
```

- #350 Intersection of Two Arrays II [link](https://leetcode.com/problems/intersection-of-two-arrays-ii/description/)
```python
class Solution:
    def intersect(self, nums1: List[int], nums2: List[int]) -> List[int]:
        dict1, dict2 = {}, {}
        for i in nums1:
            if i in dict1:
                dict1[i] += 1
            else:
                dict1[i] = 1

        for i in nums2:
            if i in dict2:
                dict2[i] += 1
            else:
                dict2[i] = 1

        output = []
        for key in dict1.keys() & dict2.keys():
            output.extend([key]*min(dict1[key], dict2[key]))
        
        return output
```


- #1446 Consecutive Characters [link](https://leetcode.com/problems/consecutive-characters/description/)
```python
class Solution:
    def maxPower(self, s: str) -> int:
        counter, max_counter = 1, 1
        for i in range(1, len(s)):
            if s[i] == s[i-1]:
                counter += 1
                max_counter = max(max_counter, counter)
            else:
                counter = 1

        return max_counter
```


- #88 Merge Sorted Array [link](https://leetcode.com/problems/merge-sorted-array/description/)
```python
class Solution:
    def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:

        a, b, write_index = m-1, n-1, m + n - 1

        while b >= 0:
            if a >= 0 and nums1[a] > nums2[b]:
                nums1[write_index] = nums1[a]
                a -= 1
            else:
                nums1[write_index] = nums2[b]
                b -= 1

            write_index -= 1
```


- #771 Jewels and Stones [link](https://leetcode.com/problems/jewels-and-stones/description/)
```python
class Solution:
    def numJewelsInStones(self, jewels: str, stones: str) -> int:
        dic = {}
        for j in jewels:
            if j in dic:
                dic[j] += 1
            else:
                dic[j] = 1
        
        counter = 0
        for c in stones:
            if c in dic.keys():
                counter += 1
        
        return counter

# one-liner

class Solution:
    def numJewelsInStones(self, jewels: str, stones: str) -> int:
    	return sum(stones.count(i) for i in jewels)
```


- #268 Missing Number [link](https://leetcode.com/problems/missing-number/description/)
```python
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        n = len(nums)
        # sum of n elements is (n * (n+1))/2 where `n` is the length of input `nums`.
        return (n * (n + 1)) // 2 - sum(nums)
```


- #557 Reverse Words in a String III [link](https://leetcode.com/problems/reverse-words-in-a-string-iii/description/)
```python
class Solution:
    def reverseWords(self, s: str) -> str:
        # bag = s.split()
        # ans = []
        # for word in bag:
        #     ans.append(word[::-1])
        # return ' '.join(ans)

        return ' '.join([word[::-1] for word in s.split()])

```


__MEDIUM__ 

- #151 Reverse Words in a String [link](https://leetcode.com/problems/reverse-words-in-a-string/description/?envType=study-plan-v2&envId=leetcode-75)
```python
class Solution:
    def reverseWords(self, s: str) -> str:
        return ' '.join(s.split()[::-1])
```

- #238 Product of Array Except Self [link](https://leetcode.com/problems/product-of-array-except-self/description/?envType=study-plan-v2&envId=leetcode-75)
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

- #334 Increasing Triplet Subsequence [link](https://leetcode.com/problems/increasing-triplet-subsequence/description/?envType=study-plan-v2&envId=leetcode-75)
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

- #443 String Compression [link](https://leetcode.com/problems/string-compression/description/?envType=study-plan-v2&envId=leetcode-75)
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
- #15 3Sum [link](https://leetcode.com/problems/3sum/)
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

- #16 3Sum Closest [link](https://leetcode.com/problems/3sum-closest/description/)
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

- #849 Maximize Distance to Closest Person [link](https://leetcode.com/problems/maximize-distance-to-closest-person/description/)
```python
'''
This problem is easy to solve, if notice that the max distance to the closest person can be calculated as numbers of empty spaces devided by two and rounded to ceil: ceil(dist/2). For example: [1, 0, 0, 0, 1] => number of zeros between ones is 3 => max distance to the closest person, if sit in between is equal to ceil(3/2) = 2. Also, we need to care about edge cases when there are lots of free seats at the start or at the end. In this case the formula is different: [0, 0, 0, 1] => number of zeros is 3 => max distance is 3, that is we don't need to divide by two.
'''
class Solution:
    def maxDistToClosest(self, seats: List[int]) -> int:
        res, dist = 0, seats.index(1)
        
        for seat in seats:
            if seat: 
                res, dist = max(res, math.ceil(dist/2)), 0
            else: 
                dist += 1
                
        return max(res, dist)
```


