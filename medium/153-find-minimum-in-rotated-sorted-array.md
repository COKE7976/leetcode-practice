# Problem : 153. Find Minimum in Rotated Sorted Array
Link : [https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/description/](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/description/)

## Solution : Binary Search
- Use binary search to iteratively check the current window, the window starting from the whole list
    - If the left most point is less than the right most point, update result, end iteration
    - Since the above condition not satisfied, if middle point is greater than the left most point, go check the right window
```python
class Solution(object):
    def findMin(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        l, r = 0, len(nums) - 1
        res = nums[0]
        while l <= r:
            if nums[l] < nums[r]:
                res = min(res, nums[l])
                break
            m = (l + r) // 2
            res = min(res, nums[m])
            if nums[m] >= nums[l]:
                l = m + 1
            else:
                r = m - 1
        return res
```
