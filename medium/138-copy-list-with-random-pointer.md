# Problem : 138. Copy List With Random Pointer
Link : [https://leetcode.com/problems/copy-list-with-random-pointer/description/](https://leetcode.com/problems/copy-list-with-random-pointer/description/)

## Solution1 : HashTable
- Use defaultdict to create default Nodes
- Nodes of original list as the keys, values are the new nodes
```python
"""
# Definition for a Node.
class Node:
    def __init__(self, x, next=None, random=None):
        self.val = int(x)
        self.next = next
        self.random = random
"""

class Solution(object):
    def copyRandomList(self, head):
        """
        :type head: Node
        :rtype: Node
        """
        mp = defaultdict(lambda: Node(0))
        mp[None] = None

        cur = head
        while cur:
            mp[cur].val = cur.val
            mp[cur].next = mp[cur.next]
            mp[cur].random = mp[cur.random]
            cur = cur.next
        return mp[head]
```
- Time : O(n)
- Space : O(n)

## Solution2 : Nodes Insertion & Separation
- Create new node after each node
- Walk through the list, assign node.random for each new node
- Separate the old nodes and new nodes
```python
"""
# Definition for a Node.
class Node:
    def __init__(self, x, next=None, random=None):
        self.val = int(x)
        self.next = next
        self.random = random
"""

class Solution(object):
    def copyRandomList(self, head):
        """
        :type head: Node
        :rtype: Node
        """
        if head is None:
            return None

        l1 = head
        while l1:
            l2 = Node(l1.val)
            l2.next = l1.next
            l1.next = l2
            l1 = l2.next
        
        res = head.next

        l1 = head
        while l1:
            l2 = l1.next
            if l1.random is not None:
                l2.random = l1.random.next
            l1 = l2.next
        
        l1 = head
        while l1:
            l2 = l1.next
            l1.next = l2.next
            if l2.next is not None:
                l2.next = l2.next.next
            l1 = l1.next
        
        return res
```
- Time : O(n)
- Space : O(1)
