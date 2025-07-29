# Problem : 78. Subsets
Link : [https://leetcode.com/problems/subsets/description/](https://leetcode.com/problems/subsets/description/)

## Solution : Backtracking
```python
class Solution(object):
    def subsets(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        res = []
        subset = []

        def dfs(i):
            if i == len(nums):
                res.append(subset[:])
                return
            
            subset.append(nums[i])
            dfs(i + 1)
            subset.pop()
            dfs(i + 1)
        
        dfs(0)
        return res
```
- Time : O(n * $2^n$), $2^n$ subsets generated, O(n) to copy one final subset to res
- Space : O(n)
