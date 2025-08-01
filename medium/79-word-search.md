# Problem : 79. Word Search
Link : [https://leetcode.com/problems/word-search/description/](https://leetcode.com/problems/word-search/description/)

## Solution : Backtracking
- Iterate through all the nodes on the board as the start
- Then go for four directions from that node
- Keep doing the same thing, to see if one path matches the "word"
```python
class Solution(object):
    def exist(self, board, word):
        """
        :type board: List[List[str]]
        :type word: str
        :rtype: bool
        """
        ROLS, COLS = len(board), len(board[0])
        path = set() # record visited nodes

        def dfs(r, c, i):
            if i == len(word):
                return True
            
            if (r < 0 or c < 0 or
                r >= ROLS or c >= COLS or
                board[r][c] != word[i] or
                (r, c) in path):
                return False
            
            path.add((r, c))
            res = (dfs(r + 1, c, i + 1) or
                   dfs(r - 1, c, i + 1) or
                   dfs(r, c + 1, i + 1) or
                   dfs(r, c - 1, i + 1))
            path.remove((r, c))

            return res
        
        for r in range(ROLS):
            for c in range(COLS):
                if dfs(r, c, 0):
                    return True
        return False
```
- Time : O(n * $4^m$)
- Space : O(n)
