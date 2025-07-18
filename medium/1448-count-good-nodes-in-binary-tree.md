# Problem : 1448. Count Good Nodes in Binary Tree
Link : [https://leetcode.com/problems/count-good-nodes-in-binary-tree/description/](https://leetcode.com/problems/count-good-nodes-in-binary-tree/description/)

## Solution1 : DFS
- Keep track of the maxVal in recursion, which is checking the maxVal along the path till current node
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def goodNodes(self, root):
        """
        :type root: TreeNode
        :rtype: int
        """
        def dfs(node, maxVal):
            if not node:
                return 0
            
            res = 1 if node.val >= maxVal else 0

            maxVal = max(node.val, maxVal)
            res += dfs(node.left, maxVal)
            res += dfs(node.right, maxVal)

            return res
        
        return dfs(root, root.val)
```
- Time : O(n)
- Space : O(n)

## Solution2 : BFS
- Double ended queue, only in Python 3
- Walk through each node by layer from left to right, and append its left & right child to the deque along with the maxVal
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def goodNodes(self, root: TreeNode) -> int:
        res = 0
        queue = collections.deque([(root, -float('inf'))])

        while queue:
            node, maxVal = queue.popleft()
            if node.val >= maxVal:
                res += 1
            
            maxVal = max(node.val, maxVal)
            if node.left:
                queue.append((node.left, maxVal))
            if node.right:
                queue.append((node.right, maxVal))
        
        return res
```
- Time : O(n)
- Space : O(n)
