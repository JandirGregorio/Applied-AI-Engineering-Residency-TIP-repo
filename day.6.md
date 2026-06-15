# Day 6

## 238. Product of Array Except Self Python solution 

```py
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        '''
        Calculate every product to the left of the array
        since there is nothing to the left of the 0th el, assume there is a one at the '-1' ele

        [1, 2, 3, 4] -> [1, 1, 2, 6]

        Calculate every product to the right of the array starting at n, where n is the last element (reverse traverse)
        [1, 2, 3, 4] -> [24, 12, 4, 1]

        multiple the two indivial arrays

        return result array
        '''

        productArray = [ 1 ]
        leftProduct = 1
        n = len(nums) - 1
        for i in range(n):
            num = nums[i]
            leftProduct *= num
            productArray.append(leftProduct)
        rightProduct = 1
        for i in range(n, -1, -1):
            productArray[i] = rightProduct * productArray[i]
            rightProduct *= nums[i]
        return productArray

```