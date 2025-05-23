# Problem : 1. Two Sum
Link : [https://leetcode.com/problems/two-sum/description/](https://leetcode.com/problems/two-sum/description/)

## Solution : Hash Table
- Key : Numbers in input list
- Val : Index of the number
```python
class Solution(object):
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        mp = {}
        for i, n in enumerate(nums):
            diff = target - n
            if diff in mp:
                return [mp[diff], i]
            mp[n] = i
        return []
```
- Time : O(n)
- Space : O(n)
