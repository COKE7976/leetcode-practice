# Problem : 230. Kth Smallest Integer in BST
Link : [https://leetcode.com/problems/kth-smallest-element-in-a-bst/description/](https://leetcode.com/problems/kth-smallest-element-in-a-bst/description/)

## Solution1 : Inorder Traversal through a List
- Construct a list by visiting all the nodes in the order of "left -> curr -> right"
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def kthSmallest(self, root, k):
        """
        :type root: Optional[TreeNode]
        :type k: int
        :rtype: int
        """
        res = []

        def dfs(node):
            if not node:
                return
            
            dfs(node.left)
            res.append(node.val)
            dfs(node.right)
        
        dfs(root)
        return res[k - 1]
```
- Time : O(n)
- Space : O(n)

## Solution2 : DFS in Recursion
- Inorder traversal, recursively call left node, process current node, recursively call right node
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def kthSmallest(self, root, k):
        """
        :type root: Optional[TreeNode]
        :type k: int
        :rtype: int
        """
        self.res = root.val
        self.count = k

        def dfs(node):
            if not node:
                return
            
            dfs(node.left)
            self.count -= 1
            if self.count == 0:
                self.res = node.val
                return
            dfs(node.right)
        
        dfs(root)
        return self.res
```
- Time : O(n)
- Space : O(n)

## Solution3 : DFS in Iteration
- Inorder traversal, push current node then go left, if no left, process current node, then go right
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def kthSmallest(self, root, k):
        """
        :type root: Optional[TreeNode]
        :type k: int
        :rtype: int
        """
        stack = []
        node = root

        while stack or node:
            while node:
                stack.append(node)
                node = node.left
            
            node = stack.pop()
            k -= 1
            if k == 0:
                return node.val
            
            node = node.right
```
- Time : O(n)
- Space : O(n)
