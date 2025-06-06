# Problem : 853. Car Fleet
Link : [https://leetcode.com/problems/car-fleet/description/](https://leetcode.com/problems/car-fleet/description/)

[ Fleet ] A fleet is a group of one or more cars that reach the target together

## Solution1 : Iteration
- Iterate through the cars by their positions, starting from the one closest to the target
- A new fleet forms when the current car takes more time to reach the target than the car ahead
- A single car always forms its own fleet
```python
class Solution(object):
    def carFleet(self, target, position, speed):
        """
        :type target: int
        :type position: List[int]
        :type speed: List[int]
        :rtype: int
        """
        pair = [(p, s) for p, s in zip(position, speed)]
        pair.sort(reverse=True)
        fleets = 0
        prevTime = -1
        for p, s in pair:
            currTime = float(target - p) / s
            if currTime > prevTime:
                fleets += 1
                prevTime = currTime
        return fleets
```

## Solution2 : Stack
- Iterate through the cars by their positions, starting from the one closest to the target
- Use a stack to keep track of each fleet's arrival time; a new fleet is added if the current car cannot catch up to the one ahead
```python
class Solution(object):
    def carFleet(self, target, position, speed):
        """
        :type target: int
        :type position: List[int]
        :type speed: List[int]
        :rtype: int
        """
        pair = [(p, s) for p, s in zip(position, speed)]
        pair.sort(reverse=True)
        stack = []
        for p, s in pair:
            stack.append(float(target - p) / s)
            if len(stack) > 1 and stack[-1] <= stack[-2]:
                stack.pop()
        return len(stack)
```
