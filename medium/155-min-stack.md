# Problem : 155. Min Stack
Link : [https://leetcode.com/problems/min-stack/description/](https://leetcode.com/problems/min-stack/description/)

## Solution1 : Two Stacks
- One as usual stack
- The other one is the min stack, which keeps the minimum value seen so far
```python
class MinStack(object):

    def __init__(self):
        self.stack = []
        self.minStack = []

    def push(self, val):
        """
        :type val: int
        :rtype: None
        """
        self.stack.append(val)
        self.minStack.append(min(val, self.minStack[-1] if self.minStack else val))

    def pop(self):
        """
        :rtype: None
        """
        self.stack.pop()
        self.minStack.pop()

    def top(self):
        """
        :rtype: int
        """
        return self.stack[-1]

    def getMin(self):
        """
        :rtype: int
        """
        return self.minStack[-1]
```
- Time : O(1)
- Space : O(n)

## Solution2 : Stack + Differential Storage

```python
class MinStack(object):

    def __init__(self):
        self.min = float('inf')
        self.stack = []

    def push(self, val):
        """
        :type val: int
        :rtype: None
        """
        if not self.stack:
            self.stack.append(0)
            self.min = val
        else:
            self.stack.append(val - self.min)
            if val < self.min:
                self.min = val

    def pop(self):
        """
        :rtype: None
        """
        if not self.stack:
            return
        
        pop = self.stack.pop()
        if pop < 0:
            self.min = self.min - pop

    def top(self):
        """
        :rtype: int
        """
        top = self.stack[-1]
        if top > 0:
            return top + self.min
        else:
            return self.min

    def getMin(self):
        """
        :rtype: int
        """
        return self.min
```
- Time : O(1)
- Space : O(n)
