# Problem : 621. Task Scheduler
Link : [https://leetcode.com/problems/task-scheduler/description/](https://leetcode.com/problems/task-scheduler/description/)

## Solution1 : MaxHeap + DeQue
- First create a HashTable, mapping characters with their frequency
- Build a max heap with the frequencies
- Each time, pop a job from max heap
  - If having remaining work, push back to the deque in format \[remaining_freq, next_available_window\]
  - If the head of deque can be executed, push back to the maxHeap
```python
class Solution:
    def leastInterval(self, tasks: List[str], n: int) -> int:
        counts = Counter(tasks)
        maxHeap = [-cnt for cnt in counts.values()]
        heapq.heapify(maxHeap)

        queue = deque()
        time = 0
        while maxHeap or queue:
            time += 1

            if maxHeap:
                freq = heapq.heappop(maxHeap)
                if freq < -1:
                    queue.append([freq + 1, time + n])
            
            if queue and queue[0][1] <= time:
                heapq.heappush(maxHeap, queue.popleft()[0])
        
        return time
```
- Time : O(n), since only 26 characters, O(nlog26) = O(n)
- Space : O(1), since only 26 characters

## Greedy
- Spread out the most frequent task as far apart as possible
- Then minimize idle slots
- A _ _ A _ _ A
  - Can all the idle slots be filled?
```python
class Solution(object):
    def leastInterval(self, tasks, n):
        """
        :type tasks: List[str]
        :type n: int
        :rtype: int
        """
        count = [0] * 26
        for t in tasks:
            count[ord(t) - ord('A')] += 1
        count.sort()

        maxFreq = count[25]
        idleSlots = (maxFreq - 1) * n

        for i in range(24, -1, -1):
            idleSlots -= min(maxFreq - 1, count[i])
        
        return max(0, idleSlots) + len(tasks)
```
- Time : O(n)
- Space : O(1)
