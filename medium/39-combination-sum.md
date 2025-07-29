# Problem : 39. Combination Sum
Link : [https://leetcode.com/problems/combination-sum/description/](https://leetcode.com/problems/combination-sum/description/)

## Solution : Backtracking
```python
class Solution(object):
    def combinationSum(self, candidates, target):
        """
        :type candidates: List[int]
        :type target: int
        :rtype: List[List[int]]
        """
        res = []

        def dfs(i, curr, total):
            if total == target:
                res.append(curr[:])
                return
            if i == len(candidates) or total > target:
                return
            
            curr.append(candidates[i])
            dfs(i, curr, total + candidates[i])
            curr.pop()
            dfs(i + 1, curr, total)
        
        dfs(0, [], 0)
        return res
```
- Time : O(n ^ (t / min_val))
  - `t` = target value
  - `min_val` = smallest candidate
  - the number of combinations can grow very quickly with larger `target` or smaller `min_val`
- Space : O(n ^ (t / min_val))
