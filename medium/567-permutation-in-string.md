# Problem : 567. Permutation in String
Link : [https://leetcode.com/problems/permutation-in-string/description/](https://leetcode.com/problems/permutation-in-string/description/)

## Solution : Hash Table + Silding Window
```python
class Solution(object):
    def checkInclusion(self, s1, s2):
        """
        :type s1: str
        :type s2: str
        :rtype: bool
        """
        if len(s1) > len(s2):
            return False

        mp1, mp2 = {}, {}
        for i in range(len(s1)):
            mp1[s1[i]] = mp1.get(s1[i], 0) + 1
            mp2[s2[i]] = mp2.get(s2[i], 0) + 1

        if mp1 == mp2:
            return True

        for i in range(len(s1), len(s2)):
            left = s2[i - len(s1)]
            right = s2[i]

            mp2[left] -= 1
            if mp2[left] == 0:
                del mp2[left]

            mp2[right] = mp2.get(right, 0) + 1

            if mp1 == mp2:
                return True

        return False
```
- Time : O(n)
- Space : O(1)
