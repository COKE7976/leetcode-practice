# Problem : 853. Car Fleet
Link : [https://leetcode.com/problems/car-fleet/description/](https://leetcode.com/problems/car-fleet/description/)

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
        for car in pair:
            p = car[0]
            s = car[1]
            currTime = float(target - p) / s
            if currTime > prevTime:
                fleets += 1
                prevTime = currTime
        return fleets
```
