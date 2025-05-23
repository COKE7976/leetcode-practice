# Problem: 217. Contains Duplicate
**Link:** [https://leetcode.com/problems/contains-duplicate/description/](https://leetcode.com/problems/contains-duplicate/description/)

---

# Solution1 : HashSet

```python
class Solution(object):
    def containsDuplicate(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        seen = set()
        for n in nums:
            if n in seen:
                return True
            seen.add(n)
        
        return False
```

# Solution2 : Length of HashSet

```python
class Solution(object):
    def containsDuplicate(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        return len(set(nums)) < len(nums)
```
