# Problem : 90. Subsets II
Link : [https://leetcode.com/problems/subsets-ii/description/](https://leetcode.com/problems/subsets-ii/description/)

## Solution : Backtracking
- Use one index to track, keep moving forward to visit/skip each elements inside the input list
- Two branch recursion
  - One for checking everything
  - One skip duplicates
```python
class Solution(object):
    def subsetsWithDup(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        res = []
        nums.sort()

        def backtrack(i, subset):
            if i == len(nums):
                res.append(subset[:])
                return
            
            subset.append(nums[i])
            backtrack(i + 1, subset)
            subset.pop()

            while i + 1 < len(nums) and nums[i] == nums[i + 1]:
                i += 1
            backtrack(i + 1, subset)
        
        backtrack(0, [])
        return res
```
- Time : O(n * $2^n$), two branch recursion
- Space : O(n), recursive call
