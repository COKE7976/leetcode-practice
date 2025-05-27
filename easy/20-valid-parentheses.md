# Problem : 20. Valid Parentheses
Link [https://leetcode.com/problems/valid-parentheses/description/](https://leetcode.com/problems/valid-parentheses/description/)

## Solution : Stack

```python
class Solution(object):
    def isValid(self, s):
        """
        :type s: str
        :rtype: bool
        """
        stack = []
        closeToOpen = {'}':'{', ']':'[', ')':'('}
        for c in s:
            if c in closeToOpen:
                if stack and stack[-1] == closeToOpen[c]:
                    stack.pop()
                else:
                    return False
            else:
                stack.append(c)
        return True if not stack else False
```
- Time : O(n)
- Space : O(n)
