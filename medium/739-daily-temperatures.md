# Problem : 739. Daily Temperatures
Link : [https://leetcode.com/problems/daily-temperatures/description/](https://leetcode.com/problems/daily-temperatures/description/)

## Solution : Stack
- Inside the result, there can be element which is 0 (no higher temperatrue in the future), so, not every index inside result needs to be updated
- Iterate through the temperature list by index
  - Keep checking if current tempertrue is higher than the temperature at the top of the stack, if it is, update the result
  - Push the index of current temperture onto the stack
```python
class Solution(object):
    def dailyTemperatures(self, temperatures):
        """
        :type temperatures: List[int]
        :rtype: List[int]
        """
        n = len(temperatures)
        res = [0] * n
        stack = []
        for i in range(n):
            while stack and temperatures[i] > temperatures[stack[-1]]:
                index = stack.pop()
                res[index] = i - index
            stack.append(i)
        return res
```
- Time : O(n)
- Space : O(n)
