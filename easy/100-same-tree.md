# Problem : 100. Same Tree
Link : [https://leetcode.com/problems/same-tree/description/](https://leetcode.com/problems/same-tree/description/)

## Solution1 : DFS in Recursion
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def isSameTree(self, p, q):
        """
        :type p: Optional[TreeNode]
        :type q: Optional[TreeNode]
        :rtype: bool
        """
        if not p and not q:
            return True
        
        if p and q and p.val == q.val:
            return self.isSameTree(p.left, q.left) and self.isSameTree(p.right, q.right)
        else:
            return False
```
- Time : O(n)
- Space : O(n)

## Solution2: DFS in Iteration
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def isSameTree(self, p, q):
        """
        :type p: Optional[TreeNode]
        :type q: Optional[TreeNode]
        :rtype: bool
        """
        stack = [(p, q)]
        while stack:
            n1, n2 = stack.pop()

            if not n1 and not n2:
                continue
            if not n1 or not n2 or n1.val != n2.val:
                return False
            
            stack.append((n1.right, n2.right))
            stack.append((n1.left, n2.left))
        
        return True
```
- Time : O(n)
- Space : O(n)
