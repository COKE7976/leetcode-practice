# Problem : 287. Find the Diplicate Number
Link : [https://leetcode.com/problems/find-the-duplicate-number/description/](https://leetcode.com/problems/find-the-duplicate-number/description/)

## Solution : Floyd's Tortoise and Hare algorithm
```python
class Solution(object):
    def findDuplicate(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        slow, fast = 0, 0
        while True:
            slow = nums[slow]
            fast = nums[nums[fast]]
            if slow == fast:
                break
        
        finder = 0
        while finder != slow:
            slow = nums[slow]
            finder = nums[finder]
        
        return finder
```
- Time : O(n)
- Space : O(1)
