# Problem : 22. Generate Parentheses
Link : [https://leetcode.com/problems/generate-parentheses/description/](https://leetcode.com/problems/generate-parentheses/description/)

## Solution : Backtracking

```python
class Solution(object):
    def generateParenthesis(self, n):
        """
        :type n: int
        :rtype: List[str]
        """
        stack = []
        res = []

        def backtrack(openN, closeN):
            if openN == closeN == n:
                res.append("".join(stack))
                return
            
            if openN < n:
                stack.append('(')
                backtrack(openN + 1, closeN)
                stack.pop()
            if closeN < openN:
                stack.append(')')
                backtrack(openN, closeN + 1)
                stack.pop()
        
        backtrack(0, 0)
        return res
```
- Time : $$
\mathcal{O}\left(\frac{4^n}{\sqrt{n}}\right)
$$
- Space : O(n)
