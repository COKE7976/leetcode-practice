# Problem : 105. Construct Binary Tree from Preorder and Inorder Traversal
Link : [https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/description/](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/description/)

## Solution1 : DFS in Recursion with Hash Table
- Preorder : root -> left -> right
- Inorder : left -> root -> right
- First node of the preorder list is the root node, then check the inorder list, the nodes sit at the left side of the root node are the left childs
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def buildTree(self, preorder, inorder):
        """
        :type preorder: List[int]
        :type inorder: List[int]
        :rtype: Optional[TreeNode]
        """
        indices = {val : idx for idx, val in enumerate(inorder)}
        self.preIdx = 0

        def dfs(l, r):
            if l > r:
                return None
            
            root = TreeNode(preorder[self.preIdx])
            mid = indices[preorder[self.preIdx]]
            self.preIdx += 1

            root.left = dfs(l, mid - 1)
            root.right = dfs(mid + 1, r)

            return root
        
        return dfs(0, len(preorder) - 1)
```
- Time : O(n), we use hash table to keep track of the indices of inorder, otherwise, the time complexity would be O($n^2$) since each recusion has to find the index of mid, which costs O(n) time
- Space : O(n)
