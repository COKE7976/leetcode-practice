# Problem : 215. Kth Largest Element in an Array
Link : [https://leetcode.com/problems/kth-largest-element-in-an-array/description/](https://leetcode.com/problems/kth-largest-element-in-an-array/description/)

## Solution1 : MinHeap
```python
class Solution(object):
    def findKthLargest(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: int
        """
        return heapq.nlargest(k, nums)[-1]
```
- Time : O(nlogk), insert n times into a heap of size k
- Space : O(k)
```python
nums = [5, 1, 8, 3, 9, 2]
largest_three = heapq.nlargest(3, nums)
print(largest_three)  # [9, 8, 5]

nums = [5, 1, 8, 3, 9, 2]
smallest_three = heapq.nsmallest(3, nums)
print(smallest_three)  # [1, 2, 3]

people = [
    {'name': 'Alice', 'age': 30},
    {'name': 'Bob', 'age': 25},
    {'name': 'Charlie', 'age': 35},
]

# Oldest person
oldest = heapq.nlargest(1, people, key=lambda x: x['age'])
print(oldest)  # [{'name': 'Charlie', 'age': 35}]

# Youngest two
youngest = heapq.nsmallest(2, people, key=lambda x: x['age'])
print(youngest)
# [{'name': 'Bob', 'age': 25}, {'name': 'Alice', 'age': 30}]
```

## Solution2 : Quick Select
LeetCode gives "Time Limit Exceeded"..
```python
class Solution(object):
    def findKthLargest(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: int
        """
        target = len(nums) - k

        def quickSelect(l, r):
            pivot = nums[r]
            p = l
            for i in range(l, r):
                if nums[i] <= pivot:
                    nums[p], nums[i] = nums[i], nums[p]
                    p += 1
            nums[p], nums[r] = nums[r], nums[p]
                
            if target < p:
                return quickSelect(l, p - 1)
            elif target > p:
                return quickSelect(p + 1, r)
            else:
                return nums[p]
        
        return quickSelect(0, len(nums) - 1)
```
- Time : O(n) in average, O($n^2$) in worst case
- Space : O(n)
