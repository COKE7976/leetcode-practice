# Problem : 3. Longest Substring Without Repeating Characters
Link : [https://leetcode.com/problems/longest-substring-without-repeating-characters/description/](https://leetcode.com/problems/longest-substring-without-repeating-characters/description/)

## Solution : Sliding Window
- Two pointers
  - one keeps moving forward
  - one moves until duplicate is removed
```python
class Solution(object):
    def lengthOfLongestSubstring(self, s):
        """
        :type s: str
        :rtype: int
        """
        seen = set()
        res = 0
        l = 0
        for r in range(len(s)):
            while s[r] in seen:
                seen.remove(s[l])
                l += 1
            seen.add(s[r])
            res = max(res, r - l + 1)
        
        return res
```
- Time : O(n)
- Space : O(n)
