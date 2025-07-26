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
