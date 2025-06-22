# Problem : 875. Koko Eating Bananas
Link : [https://leetcode.com/problems/koko-eating-bananas/description/](https://leetcode.com/problems/koko-eating-bananas/description/)

## Solution : Binary Search
- Binary search, range from 1 to the maximum pile size (eating minimum 1 banana per hour to eating the maximum pile in an hour)
```python
class Solution(object):
    def minEatingSpeed(self, piles, h):
        """
        :type piles: List[int]
        :type h: int
        :rtype: int
        """
        l, r = 1, max(piles)
        res = 0
        while l <= r:
            m = (l + r) // 2
            time = sum((p + m - 1) // m for p in piles)
            if time <= h:
                res = m
                r = m - 1
            else:
                l = m + 1
        return res
```
