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

## Solution2 : Bucket Sort
- Use bucket sort
    - index : weight
    - value : number of stones
- Examine through all the buckets starting from maxWeight
```python
class Solution(object):
    def lastStoneWeight(self, stones):
        """
        :type stones: List[int]
        :rtype: int
        """
        maxWeight = max(stones)
        bucket = [0] * (maxWeight + 1)
        for s in stones:
            bucket[s] += 1

        current = maxWeight
        while current:
            if current > 0 and bucket[current] % 2 == 0: # if the bucket contains even number, meets the condition that x == y, so smash (skip) the stones
                current -= 1
                continue
            
            nextHeavy = current - 1
            while nextHeavy > 0 and bucket[nextHeavy] == 0:
                nextHeavy -= 1
            
            if nextHeavy == 0:
                return current
            
            bucket[current] -= 1
            bucket[nextHeavy] -= 1
            newStone = current - nextHeavy
            bucket[newStone] += 1

            current = max(nextHeavy, newStone)
        
        return 0
```
- Time : O(n)
- Space : O(n)
