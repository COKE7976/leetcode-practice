# Problem : 146. LRU Cache
Link : [https://leetcode.com/problems/lru-cache/description/](https://leetcode.com/problems/lru-cache/description/)

## Solution1 : Doubly Linked List
- DummyLeft <--> LRU <--> Node <--> Node <--> MRU <--> DummyRight
- Insert as MRU
- Revmoe the LRU
- Use Hash Table
    - Key : key
    - Val : Node
```python
class Node:
    def __init__(self, key, val):
        self.key, self.val = key, val
        self.prev = self.next = None

class LRUCache(object):

    def __init__(self, capacity):
        """
        :type capacity: int
        """
        self.cap = capacity
        self.cache = {}
        self.dummyLeft, self.dummyRight = Node(0, 0), Node(0, 0)
        self.dummyLeft.next, self.dummyRight.prev = self.dummyRight, self.dummyLeft
    
    def remove(self, node):
        prev, nxt = node.prev, node.next
        prev.next, nxt.prev = nxt, prev
    
    def insert(self, node):
        prev, nxt = self.dummyRight.prev, self.dummyRight
        prev.next = nxt.prev = node
        node.prev, node.next = prev, nxt

    def get(self, key):
        """
        :type key: int
        :rtype: int
        """
        if key in self.cache:
            self.remove(self.cache[key])
            self.insert(self.cache[key])
            return self.cache[key].val
        return -1

    def put(self, key, value):
        """
        :type key: int
        :type value: int
        :rtype: None
        """
        if key in self.cache:
            self.remove(self.cache[key])
            del self.cache[key]
        self.cache[key] = Node(key, value)
        self.insert(self.cache[key])

        if len(self.cache) > self.cap:
            lru = self.dummyLeft.next
            self.remove(lru)
            del self.cache[lru.key]

# Your LRUCache object will be instantiated and called as such:
# obj = LRUCache(capacity)
# param_1 = obj.get(key)
# obj.put(key,value)
```
- Time : O(1) for get() & set()
- Space : O(n)

## Solution2 : OrderedDict()
- Only in Python3
```python
class LRUCache:

    def __init__(self, capacity: int):
        self.cache = OrderedDict()
        self.cap = capacity

    def get(self, key: int) -> int:
        if key not in self.cache:
            return -1
        self.cache.move_to_end(key)
        return self.cache[key]

    def put(self, key: int, value: int) -> None:
        if key in self.cache:
            self.cache.move_to_end(key)
        self.cache[key] = value

        if len(self.cache) > self.cap:
            self.cache.popitem(last=False)


# Your LRUCache object will be instantiated and called as such:
# obj = LRUCache(capacity)
# param_1 = obj.get(key)
# obj.put(key,value)
```
- Time : O(1) for get() & set()
- Space : O(n)
