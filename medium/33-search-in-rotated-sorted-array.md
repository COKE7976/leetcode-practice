# Problem : 33. Search in Rotated Sorted Array
Link : [https://leetcode.com/problems/search-in-rotated-sorted-array/description/](https://leetcode.com/problems/search-in-rotated-sorted-array/description/)

## Solution : Binary Search
- Binary search, when having the middle point
    - Check if it's the left or the right window is in ascending order, go for the ascending order one
        - Check if the target is within or outside the window in ascending order
```python
class Solution(object):
    def search(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        l, r = 0, len(nums) - 1
        while l <= r:
            m = (l + r) // 2
            if nums[m] == target:
                return m
            
            if nums[l] <= nums[m]:
                if target < nums[l] or target > nums[m]:
                    l = m + 1
                else:
                    r = m - 1
            else:
                if target < nums[m] or target > nums[r]:
                    r = m - 1
                else:
                    l = m + 1
        return -1
```
