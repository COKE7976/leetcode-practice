# Problem : 105. Construct Binary Tree from Preorder and Inorder Traversal
Link : [https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/description/](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/description/)

## Solution1 : Recursion
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
        if not preorder or not inorder:
            return None
        
        root = TreeNode(preorder[0])
        mid = inorder.index(preorder[0])

        root.left = self.buildTree(preorder[1 : mid + 1], inorder[ : mid])
        root.right = self.buildTree(preorder[mid + 1 : ], inorder[mid + 1 : ])

        return root
```
- Time : O($n^2$)
- Space : O(n)
