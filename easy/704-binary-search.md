# Problem : 704. Binary Search
Link : [https://leetcode.com/problems/binary-search/description/](https://leetcode.com/problems/binary-search/description/)

## Solution :

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
            elif nums[m] < target:
                l = m + 1
            else:
                r = m - 1
        return -1
```
