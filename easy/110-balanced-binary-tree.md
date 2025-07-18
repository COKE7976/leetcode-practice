# Problem : 110. Balanced Binary Tree
Link : [https://leetcode.com/problems/balanced-binary-tree/description/](https://leetcode.com/problems/balanced-binary-tree/description/)

## Solution1 : DFS in Recursion
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def isBalanced(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: bool
        """
        def dfs(root):
            if not root:
                return [True, 0]
            
            left = dfs(root.left)
            right = dfs(root.right)
            balanced = left[0] and right[0] and abs(left[1] - right[1]) <= 1

            return [balanced, 1 + max(left[1], right[1])]
        
        return dfs(root)[0]
```

## Solution2 : DFS in Iteration
- Post-order traversal : left -> right -> node
    - Since we use the current node to decide whether to visit its right child or process the node itself, we need to track the last visited node to determine if the right child has already been visited.
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def isBalanced(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: bool
        """
        stack = []
        depth = {}
        node = root
        last = None

        while stack or node:
            if node:
                stack.append(node)
                node = node.left
            else:
                node = stack[-1]
                if node.right and last != node.right:
                    node = node.right
                else:
                    stack.pop()

                    left = depth.get(node.left, 0)
                    right = depth.get(node.right, 0)

                    if abs(left - right) > 1:
                        return False
                    
                    depth[node] = 1 + max(left, right)
                    last = node
                    node = None
        
        return True
```
