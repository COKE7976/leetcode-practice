# Problem : 703. Kth Largest Element in a Stream
Link : [https://leetcode.com/problems/kth-largest-element-in-a-stream/description/](https://leetcode.com/problems/kth-largest-element-in-a-stream/description/)

## Solution : MinHeap
```python
class KthLargest(object):

    def __init__(self, k, nums):
        """
        :type k: int
        :type nums: List[int]
        """
        self.minHeap, self.k = nums, k
        heapq.heapify(self.minHeap)
        while len(self.minHeap) > self.k:
            heapq.heappop(self.minHeap)

    def add(self, val):
        """
        :type val: int
        :rtype: int
        """
        heapq.heappush(self.minHeap, val)
        if len(self.minHeap) > self.k:
            heapq.heappop(self.minHeap)
        return self.minHeap[0]
```
- Time : O(n * logk)
- Space : O(k)

```python
# build max heap using heapq
push : heapq.heappush(queue, -val)
pop  : -heapq.heappop(queue, val)
```
