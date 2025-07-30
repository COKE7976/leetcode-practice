# Problem : 40. Combination Sum II
Link : [https://leetcode.com/problems/combination-sum-ii/description/](https://leetcode.com/problems/combination-sum-ii/description/)

## Solution1 : Backtracking
- Two branch recursion
- Since the elements have duplicates, for skipping branch, one more condition has to set to skip those duplicates
```python
class Solution(object):
    def combinationSum2(self, candidates, target):
        """
        :type candidates: List[int]
        :type target: int
        :rtype: List[List[int]]
        """
        res = []
        candidates.sort()
        
        def dfs(i, curr, total):
            if total == target:
                res.append(curr[:])
                return

            if total > target or i == len(candidates):
                return

            curr.append(candidates[i])
            dfs(i + 1, curr, total + candidates[i])
            curr.pop()

            while i + 1 < len(candidates) and candidates[i] == candidates[i + 1]:
                i += 1
            dfs(i + 1, curr, total)

        dfs(0, [], 0)
        return res
```
- Time : O(n * $2^n$), two branch recursion
- Space : O(n)

## Solution2 : Backtracking Optimal Ver
```python
class Solution(object):
    def combinationSum2(self, candidates, target):
        """
        :type candidates: List[int]
        :type target: int
        :rtype: List[List[int]]
        """
        res = []
        candidates.sort()

        def dfs(idx, curr, total):
            if total == target:
                res.append(curr[:])
                return
            for i in range(idx, len(candidates)):
                if i > idx and candidates[i] == candidates[i - 1]:
                    continue
                if total + candidates[i] > target:
                    break

                curr.append(candidates[i])
                dfs(i + 1, curr, total + candidates[i])
                curr.pop()

        dfs(0, [], 0)
        return res
```
- Time : O(n * $2^n$), two branch recursion
- Space : O(n)
