# Problem : 102. Binary Tree Level Order Traversal
Link : [https://leetcode.com/problems/binary-tree-level-order-traversal/description/](https://leetcode.com/problems/binary-tree-level-order-traversal/description/)

## Solution1 : DFS
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def levelOrder(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: List[List[int]]
        """
        res = []

        def dfs(node, depth):
            if not node:
                return None
            if len(res) == depth:
                res.append([])
            
            res[depth].append(node.val)
            
            dfs(node.left, 1 + depth)
            dfs(node.right, 1 + depth)
        
        dfs(root, 0)
        return res
```
- Time : O(n)
- Space : O(n)

## Solution2 : BFS
- Double ended queue, collections.deque(), only in python 3
    - queue.append(), queue.appendleft(), queue.pop(), queue.popleft()
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        queue = collections.deque()
        queue.append(root)
        res = []
        while queue:
            level = []
            size = len(queue)
            for _ in range(size):
                node = queue.popleft()
                if node:
                    level.append(node.val)
                    queue.append(node.left)
                    queue.append(node.right)
            if level:
                res.append(level)
        
        return res
```
- Time : O(n)
- Space : O(n)
