# Day 2

## Two Sum -- JavaScript Solution:

```js
javascript
function twoSum(nums, target) {
  for (let i = 0; i < nums.length; i++) {
    for (let j = i + 1; j < nums.length; j++) {
      if (nums[i] + nums[j] === target) {
        return [i, j];
      }
    }
  }
}
```

## Python solution

```py
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i in range(len(nums)):
            num1 = nums[i]
            for j in range(i + 1, len(nums)):
                num2 = nums[j]
                if (num1 + num2 == target):
                    return [i, j]
```

### What it does (English)

This function finds and returns the index of two numbers that sum up to `target`.

## Best Time to Buy and Sell Stock -- JavaScript Solution:

```js
function maxProfit(prices) {
  let minPrice = Infinity;
  let maxProfit = 0;
  for (let i = 0; i < prices.length; i++) {
    if (prices[i] < minPrice) {
      minPrice = prices[i];
    } else if (prices[i] - minPrice > maxProfit) {
      maxProfit = prices[i] - minPrice;
    }
  }
  return maxProfit;
}
```

## Python solution

```py
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        minPrice = float('inf')
        maxProfit = 0
        for price in prices:
            currProfit = price - minPrice
            if price < minPrice:
                minPrice = price
            elif currProfit > maxProfit:
                maxProfit = currProfit
        return maxProfit
```

### What it does (English)

It returns the maximum profit you can get by buying the cheapest stock and selling it in the future on a different day.