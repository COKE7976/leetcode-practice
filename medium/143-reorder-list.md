# Problem : 143. Reorder List
Link : [https://leetcode.com/problems/reorder-list/description/](https://leetcode.com/problems/reorder-list/description/)

## Solution :
- Break the list in half
- Reverse the second half
- Merge two lists back
```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def reorderList(self, head):
        """
        :type head: Optional[ListNode]
        :rtype: None Do not return anything, modify head in-place instead.
        """
        slow, fast = head, head.next
        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next
        
        second = slow.next
        slow.next = None 'end the first half'
        prev = None
        while second:
            second.next, prev, second = prev, second, second.next
        
        first, second = head, prev
        while second:
            tmp1, tmp2 = first.next, second.next
            first.next = second
            second.next = tmp1
            first, second = tmp1, tmp2
```
- Time : O(n)
- Space : O(1)
