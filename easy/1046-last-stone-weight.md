# Problem : 1046. Last Stone Weight
Link : [https://leetcode.com/problems/last-stone-weight/description/](https://leetcode.com/problems/last-stone-weight/description/)

## Solution1 : MaxHeap
```python
class Solution(object):
    def lastStoneWeight(self, stones):
        """
        :type stones: List[int]
        :rtype: int
        """
        queue = [-s for s in stones]
        heapq.heapify(queue)

        while len(queue) > 1:
            first = heapq.heappop(queue)
            second = heapq.heappop(queue)
            if first != second:
                heapq.heappush(queue, first - second)
            
        return 0 if not queue else -queue[0]
```
- Time : O(nlogn)
- Space : O(n)

