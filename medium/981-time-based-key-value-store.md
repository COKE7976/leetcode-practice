# Problem : 981. Time Based Key-Value Store
Link [https://leetcode.com/problems/time-based-key-value-store/description/](https://leetcode.com/problems/time-based-key-value-store/description/)

## Solution : HashTable + Binary Search
- Use HashTable to store data, and use binary search to obtain the data
```python
class TimeMap(object):

    def __init__(self):
        self.store = {}

    def set(self, key, value, timestamp):
        """
        :type key: str
        :type value: str
        :type timestamp: int
        :rtype: None
        """
        if key not in self.store:
            self.store[key] = []
        self.store[key].append([value, timestamp])

    def get(self, key, timestamp):
        """
        :type key: str
        :type timestamp: int
        :rtype: str
        """
        res = ""
        values = self.store.get(key, [])
        l, r = 0, len(values) - 1
        while l <= r:
            m = (l + r) // 2
            if values[m][1] <= timestamp:
                res = values[m][0]
                l = m + 1
            else:
                r = m - 1
        return res
```
