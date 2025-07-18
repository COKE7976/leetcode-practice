# Problem : 98. Valid Binary Search Tree
Link : [https://leetcode.com/problems/validate-binary-search-tree/description/](https://leetcode.com/problems/validate-binary-search-tree/description/)

## Solution1 : DFS
- Pass left and right boundary along with the recursion
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def isValidBST(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: bool
        """
        def dfs(node, leftVal, rightVal):
            if not node:
                return True
            if not (leftVal < node.val < rightVal):
                return False
            
            return dfs(node.left, leftVal, node.val) and dfs(node.right, node.val, rightVal)
        
        return dfs(root, -float('inf'), float('inf'))
```
- Time : O(n)
- Space : O(n)

## Solution2 : BFS
- Double ended queue, only in Python 3
- Push (node, left_boundary, right_boundary) into the queue by layer
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isValidBST(self, root: Optional[TreeNode]) -> bool:
        if not root:
            return None
        
        queue = collections.deque([(root, -float('inf'), float('inf'))])
        while queue:
            node, leftVal, rightVal = queue.popleft()
            if not (leftVal < node.val < rightVal):
                return False
            
            if node.left:
                queue.append((node.left, leftVal, node.val))
            if node.right:
                queue.append((node.right, node.val, rightVal))
        
        return True
```
- Time : O(n)
- Space : O(n)
