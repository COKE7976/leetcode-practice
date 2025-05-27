# Problem : 424. Longest Repeating Character Replacement
Link : [https://leetcode.com/problems/longest-repeating-character-replacement/](https://leetcode.com/problems/longest-repeating-character-replacement/)

## Solution1 : Sliding Window by Distinct Characters
- Iterate through each character inside the string, treat the character unchangable
- Left pointer moves on when current window can't fit the demand
```python
class Solution(object):
    def characterReplacement(self, s, k):
        """
        :type s: str
        :type k: int
        :rtype: int
        """
        chars = set(s)
        res = 0
        for c in chars:
            cCount = l = 0
            for r in range(len(s)):
                if s[r] == c:
                    cCount += 1
                while (r - l + 1) - cCount > k:
                    if s[l] == c:
                        cCount -= 1
                    l += 1
                res = max(res, r - l + 1)
        return res
```
- Time : O(m * n), m distinct characters
- Space : O(m), m distinct characters

## Solution2 : Sliding Window Optimal Version
- Keep track of the number of the most frequent character
> I personally don't get it that, why a stale `maxFreq` can work (not updating it when left pointer moves..)
```python
class Solution(object):
    def characterReplacement(self, s, k):
        """
        :type s: str
        :type k: int
        :rtype: int
        """
        cCount = {}
        maxFreq = 0
        res = 0
        l = 0
        for r in range(len(s)):
            cCount[s[r]] = 1 + cCount.get(s[r], 0)
            maxFreq = max(maxFreq, cCount[s[r]])
            while (r - l + 1) - maxFreq > k:
                cCount[s[l]] -= 1
                l += 1
            res = max(res, r - l + 1)
        return res
```
- Time : O(n)
- Space : O(m), m distinct characters
