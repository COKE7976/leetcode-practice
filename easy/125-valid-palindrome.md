# Problem : 125. Valid Palindrome
Link : [https://leetcode.com/problems/valid-palindrome/description/](https://leetcode.com/problems/valid-palindrome/description/)

## Solution : Two Pointers
```python
class Solution(object):
    def isPalindrome(self, s):
        """
        :type s: str
        :rtype: bool
        """
        l, r = 0, len(s) - 1
        while l < r:
            while l < r and not self.isAlphaNum(s[l]):
                l += 1
            while l < r and not self.isAlphaNum(s[r]):
                r -= 1
            if s[l].lower() != s[r].lower():
                return False
            l += 1
            r -= 1
        return True
    
    def isAlphaNum(self, c):
        return (ord('a') <= ord(c) <= ord('z') or
                ord('A') <= ord(c) <= ord('Z') or
                ord('0') <= ord(c) <= ord('9'))
```
Time : O(n)
Space : O(1)
