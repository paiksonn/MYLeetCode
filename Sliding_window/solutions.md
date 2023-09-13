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

- __MEDIUM__ Max Consecutive Ones III [link](https://leetcode.com/problems/max-consecutive-ones-iii/?envType=study-plan-v2&envId=leetcode-75)
```python
class Solution:
    def longestOnes(self, A: List[int], K: int) -> int:
      left = right = 0
      
      for right in range(len(A)):
        # if we encounter a 0 the we decrement K
        if A[right] == 0:
          K -= 1
        # else no impact to K
        
        # if K < 0 then we need to move the left part of the window forward
        # to try and remove the extra 0's
        if K < 0:
          # if the left one was zero then we adjust K
          if A[left] == 0:
            K += 1
          # regardless of whether we had a 1 or a 0 we can move left side by 1
          # if we keep seeing 1's the window still keeps moving as-is
          left += 1
      
      return right - left + 1
```

