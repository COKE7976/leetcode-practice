# Problem : 121. Best Time to Buy and Sell Stock
Link : [https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/)

## Solution : Two Pointers
- Two pointers
  - one keep moving forward
  - one conditionally set
```python
class Solution(object):
    def maxProfit(self, prices):
        """
        :type prices: List[int]
        :rtype: int
        """
        res = 0
        l = 0
        for r in range(1, len(prices)):
            if prices[l] < prices[r]:
                res = max(res, prices[r] - prices[l])
            else:
                l = r
        return res
```
- Time : O(n)
- Space : O(1)
