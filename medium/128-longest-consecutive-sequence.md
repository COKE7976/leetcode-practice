# Problem : 128. Longest Consecutive Sequence

# Solution1 : Hash Set
- Put all the numbers into a set
- Iterate through the set
  - Go to next loop if (n - 1) in the set
  - Count the length of consecutive sequence starting from n
  - Update the result if needed
```python
class Solution(object):
    def longestConsecutive(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        lis = set(nums)
        res = 0
        for n in lis:
            if (n - 1) in lis:
                continue
            len = 1
            while (n + len) in lis:
                len += 1
            res = max(res, len)
        
        return res
```
- Time : O(n)
- Space : O(n)

# Solution2 : Hash Table + Range Merging
- Handle only new numbers
- Keep track of the length at the start and the end of each chain
```python
class Solution(object):
    def longestConsecutive(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        mp = defaultdict(int)
        res = 0
        for n in nums:
            if not mp[n]:
                left, right = mp[n - 1], mp[n + 1]
                mp[n] = left + right + 1
                mp[n - left] = mp[n]
                mp[n + right] = mp[n]
                res = max(res, mp[n])
        
        return res
```
- Time : O(n)
- Space : O(n)
