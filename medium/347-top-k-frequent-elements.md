# Problem : 347. Top K Frequent Elements
Link [https://leetcode.com/problems/top-k-frequent-elements/](https://leetcode.com/problems/top-k-frequent-elements/)

## Solution1 : Min Heap
- Dump all the numbers into a hash table, key = number, value = frequency of that number
- Prepare a list as the min heap
- Iterate through the hash table
  - Push tuple (frequency, number) into the min heap
  - If heap size > k, pop one element
- Prepare a list as the result, pop elements from min heap and append it after the result
```python
class Solution(object):
    def topKFrequent(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: List[int]
        """
        count = {}
        for n in nums:
            count[n] = 1 + count.get(n, 0)
        
        heap = []
        for n in count.keys():
            heapq.heappush(heap, (count[n], n))
            if len(heap) > k:
                heapq.heappop(heap)
        
        res = []
        for i in range(k):
            res.append(heapq.heappop(heap)[1])
        
        return res
```
- Time : O(nlogk), min heap push & pop take logk time
- Space  O(n + k)

## Solution2 : Bucket Sort
- Create freqTable = [[ ], [ ], [ ], [ ], [ ], ...], which is [[ ] * (n+1)]
- Perform bucket sort : index = frequency, value = number
```python
class Solution(object):
    def topKFrequent(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: List[int]
        """
        count = {}
        freqTable = [[] for i in range(len(nums) + 1)]

        for n in nums:
            count[n] = 1 + count.get(n, 0)
        for n, f in count.items():
            freqTable[f].append(n)
        
        res = []
        for i in range(len(freqTable) - 1, 0, -1):
            for n in freqTable[i]:
                res.append(n)
                if len(res) == k:
                    return res
        return []
```
Time : O(n)
Space : O(n)
