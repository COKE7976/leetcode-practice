# Problem : 238. Product of Array Except Self
Link : [https://leetcode.com/problems/product-of-array-except-self/description/](https://leetcode.com/problems/product-of-array-except-self/description/)

## Solution1 : Prefix & Suffix
- [ 1,  2,  3,  4]
- [ 1,  1,  2,  6] --> prefix
- [24, 12,  4,  1] --> suffix
- [24, 12,  8,  6] --> result
```python
class Solution(object):
    def productExceptSelf(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        n = len(nums)
        pref, suff, res = [1] * n, [1] * n, [0] * n

        for i in range(1, n):
            pref[i] = pref[i - 1] * nums[i - 1]
        for i in range(n - 2, -1, -1):
            suff[i] = suff[i + 1] * nums[i + 1]
        for i in range(n):
            res[i] = pref[i] * suff[i]
    
        return res
```
- Time : O(n)
- Space : O(n)

## Solution2 : Optimal Prefix & Suffix
- Use no extra space for prefix and suffix
```python
class Solution(object):
    def productExceptSelf(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        n = len(nums)
        res = [1] * n

        pref = 1
        for i in range(n):
            res[i] = pref
            pref *= nums[i]
        suff = 1
        for i in range(n - 1, -1, -1):
            res[i] *= suff
            suff *= nums[i]
        
        return res
```
- Time : O(n)
- Space : O(1)
