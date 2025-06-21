# Problem : 74. Search a 2D Matrix
Link : [https://leetcode.com/problems/search-a-2d-matrix/description/](https://leetcode.com/problems/search-a-2d-matrix/description/)

## Solution : Binary Search

```python
class Solution(object):
    def searchMatrix(self, matrix, target):
        """
        :type matrix: List[List[int]]
        :type target: int
        :rtype: bool
        """
        ROWS, COLS = len(matrix), len(matrix[0])
        
        l, r = 0, ROWS * COLS - 1
        while l <= r:
            m = (l + r) // 2
            rows, cols = m // COLS, m % COLS
            if matrix[rows][cols] == target:
                return True
            elif matrix[rows][cols] < target:
                l = m + 1
            else:
                r = m - 1
        return False
```
