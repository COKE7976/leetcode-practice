# Problem : 151. Evaluate Reverse Polish Notation
Link : [https://leetcode.com/problems/evaluate-reverse-polish-notation/description/](https://leetcode.com/problems/evaluate-reverse-polish-notation/description/)

## Solution : Stack
- Operand - push
- Operator - pop two numbers, perform the operation, push back the result

```python
class Solution(object):
    def evalRPN(self, tokens):
        """
        :type tokens: List[str]
        :rtype: int
        """
        stack = []
        ops = {
            '+': operator.add,
            '-': operator.sub,
            '*': operator.mul,
            '/': lambda a,b: math.trunc(operator.truediv(a, b))
        }
        for c in tokens:
            if c in ops:
                b = stack.pop()
                a = stack.pop()
                stack.append(ops[c](a, b))
            else:
                stack.append(int(c))
        return stack[0]
```
- Time : O(n)
- Space : O(n)
