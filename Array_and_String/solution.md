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
```

- __MEDIUM__ Reverse Words in a String [link](https://leetcode.com/problems/reverse-words-in-a-string/description/?envType=study-plan-v2&envId=leetcode-75)
```python
class Solution:
    def reverseWords(self, s: str) -> str:
        return ' '.join(s.split()[::-1])
```

