# Problem : 199. Binary Tree Right Side View
Link : [https://leetcode.com/problems/binary-tree-right-side-view/description/](https://leetcode.com/problems/binary-tree-right-side-view/description/)

## Solution1 : DFS
- Recursively call the dfs function, since goes to right node first, if the condition meets, that the "depth == len(res)", append the value
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def rightSideView(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: List[int]
        """
        res = []
        def dfs(node, depth):
            if not node:
                return None
            if depth == len(res):
                res.append(node.val)
            
            dfs(node.right, 1 + depth)
            dfs(node.left, 1 + depth)
        dfs(root, 0)
        return res
```
- Time : O(n)
- Space : O(n)

# Solution2 : BFS
- Double ended queue, only in Python 3
- Examine the tree layer by layer, and the last node of the layer, push its val to the res
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def rightSideView(self, root: Optional[TreeNode]) -> List[int]:
        res = []
        queue = collections.deque([root])
        while queue:
            size = len(queue)
            lastNode = None
            for _ in range(size):
                node = queue.popleft()
                if node:
                    lastNode = node
                    queue.append(node.left)
                    queue.append(node.right)
            if lastNode:
                res.append(lastNode.val)
        return res
```
- Time : O(n)
- Space : O(n)
