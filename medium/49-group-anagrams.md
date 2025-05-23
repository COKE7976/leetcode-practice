# Problem : 49. Group Anagrams
Link : [https://leetcode.com/problems/group-anagrams/description/](https://leetcode.com/problems/group-anagrams/description/)

## Solution : Hash Table
- Key : A tuple representing the count of each letter (`[a–z]`) in the string
- Value : A list of strings that share the same key (i.e., are anagrams)
```python
class Solution(object):
    def groupAnagrams(self, strs):
        """
        :type strs: List[str]
        :rtype: List[List[str]]
        """
        res = defaultdict(list)
        for s in strs:
            key = [0] * 26
            for c in s:
                key[ord(c) - ord('a')] += 1
            res[tuple(key)].append(s)
        return list(res.values())
```
- Time Complexity : O(n * k), n = number of strings, k = maximum length of a string
- Space Complexity : O(n * k), n = number of strings, k = maximum length of a string
