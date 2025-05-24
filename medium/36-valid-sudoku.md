# Problem : 36. Valid Sudoku
Link : [https://leetcode.com/problems/valid-sudoku/](https://leetcode.com/problems/valid-sudoku/)

## Solution1 : Hash Table
- Use defaultdict
  - Key : Indexes
    - Row : r (0 - 8)
    - Column : c (0 - 8)
    - Square : tuple (r // 3, c // 3)
  - Val : Hash Set
```python
class Solution(object):
    def isValidSudoku(self, board):
        """
        :type board: List[List[str]]
        :rtype: bool
        """
        rows, cols, squares = defaultdict(set), defaultdict(set), defaultdict(set)

        for r in range(9):
            for c in range(9):
                if board[r][c] == ".":
                    continue
                if (board[r][c] in rows[r] or
                    board[r][c] in cols[c] or
                    board[r][c] in squares[(r // 3, c // 3)]):
                    return False
                rows[r].add(board[r][c])
                cols[c].add(board[r][c])
                squares[(r // 3, c // 3)].add(board[r][c])
        
        return True
```
- Time : O(1) = O(9 × 9 × constant)
  - Each lookup (in set) and insertion (add) in a set takes O(1) average time.
- Space : O(1)

## Solution2 : Bitmask

```python
class Solution(object):
    def isValidSudoku(self, board):
        """
        :type board: List[List[str]]
        :rtype: bool
        """
        rows, cols, squares = [0] * 9, [0] * 9, [0] * 9

        for r in range(9):
            for c in range(9):
                if board[r][c] == ".":
                    continue
                val = int(board[r][c]) - 1
                if ((1 << val) & rows[r] or
                    (1 << val) & cols[c] or
                    (1 << val) & squares[(r // 3) * 3 + (c // 3)]):
                    return False
                rows[r] |= (1 << val)
                cols[c] |= (1 << val)
                squares[(r // 3) * 3 + (c // 3)] |= (1 << val)
        
        return True
```
- Time : O(1)
- Space : O(1)
