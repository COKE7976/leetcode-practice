# Problem : 739. Daily Temperatures
Link : [https://leetcode.com/problems/daily-temperatures/description/](https://leetcode.com/problems/daily-temperatures/description/)

## Solution : Stack
- Inside the result, there can be element which is 0 (no higher temperatrue in the future), so, not every index inside result needs to be updated
- Push (temperature, index) into the stack, when new temperature is visited
  - Check if the temperature of the top of the stack satisfy the condition, if yes, pops it and update the result
```python
class Solution(object):
    def dailyTemperatures(self, temperatures):
        """
        :type temperatures: List[int]
        :rtype: List[int]
        """
        res = [0] * len(temperatures)
        stack = []
        for i, t in enumerate(temperatures):
            while stack and t > stack[-1][0]:
                temp, index = stack.pop()
                res[index] = i - index
            stack.append((t, i))
        return res
```
- Time : O(n)
- Space : O(n)
