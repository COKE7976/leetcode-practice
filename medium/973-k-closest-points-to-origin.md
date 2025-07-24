# Problem : 973. K Closest Points to Origin
Link : [https://leetcode.com/problems/k-closest-points-to-origin/description/](https://leetcode.com/problems/k-closest-points-to-origin/description/)

## Solution : MinHeap
```python
class Solution(object):
    def kClosest(self, points, k):
        """
        :type points: List[List[int]]
        :type k: int
        :rtype: List[List[int]]
        """
        minHeap = []
        for x, y in points:
            dist = x ** 2 + y ** 2
            minHeap.append([dist, x, y])
        
        heapq.heapify(minHeap)

        res = []
        while k > 0:
            dist, x, y = heapq.heappop(minHeap)
            res.append([x, y])
            k -= 1
        
        return res
```
- Time : O(klogn)
- Space : O(n)
