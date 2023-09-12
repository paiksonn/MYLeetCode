- __EASY__ Maximum Average Subarray I [link](https://leetcode.com/problems/maximum-average-subarray-i/?envType=study-plan-v2&envId=leetcode-75)
```python
class Solution:
    def findMaxAverage(self, nums: List[int], k: int) -> float:
        best = now = sum(nums[:k])
        for i in range(k,len(nums)):
            now += nums[i] - nums[i-k]
            if now > best:
                best = now
        return best / k
```

- __MEDIUM__ Maximum Number of Vowels in a Substring of Given Length [link](https://leetcode.com/problems/maximum-number-of-vowels-in-a-substring-of-given-length/?envType=study-plan-v2&envId=leetcode-75)
```python
class Solution:
    def maxVowels(self, s: str, k: int) -> int:
        vowel_letters = 'aeiou'
        # Build the window of size k, count the number of vowels it contains.
        count = 0
        for i in range(k):
            count += int(s[i] in vowel_letters)
        answer = count
        # Slide the window to the right, focus on the added character and the
        # removed character and update "count". Record the largest "count".
        for i in range(k, len(s)):
            count += int(s[i] in vowel_letters)
            count -= int(s[i - k] in vowel_letters)
            answer = max(answer, count)
        return answer
```
