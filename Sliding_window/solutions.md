__EASY__ 

- #643 Maximum Average Subarray I [link](https://leetcode.com/problems/maximum-average-subarray-i/?envType=study-plan-v2&envId=leetcode-75)
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

__MEDIUM__ 

- #1456 Maximum Number of Vowels in a Substring of Given Length [link](https://leetcode.com/problems/maximum-number-of-vowels-in-a-substring-of-given-length/?envType=study-plan-v2&envId=leetcode-75)
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

- #1004 Max Consecutive Ones III [link](https://leetcode.com/problems/max-consecutive-ones-iii/?envType=study-plan-v2&envId=leetcode-75)
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

_ #1493 Longest Subarray of 1's After Deleting One Element [link](https://leetcode.com/problems/longest-subarray-of-1s-after-deleting-one-element/description/?envType=study-plan-v2&envId=leetcode-75)
```python
class Solution:
    def longestSubarray(self, nums: List[int]) -> int:
        n = len(nums)  # The size of the input array

        left = 0  # The left pointer of the sliding window
        zeros = 0  # Number of zeroes encountered
        ans = 0  # Maximum length of the subarray

        for right in range(n):
            if nums[right] == 0:
                zeros += 1  # Increment the count of zeroes

            # Adjust the window to maintain at most one zero in the subarray
            while zeros > 1:
                if nums[left] == 0:
                    zeros -= 1  # Decrement the count of zeroes
                left += 1  # Move the left pointer to the right

            # Calculate the length of the current subarray and update the maximum length
            ans = max(ans, right - left + 1 - zeros)

        # If the entire array is the subarray, return the size minus one; otherwise, return the maximum length
        return ans - 1 if ans == n else ans
```

