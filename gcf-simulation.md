# 1480. Running Sum of 1d Array

```py
class Solution:
    def runningSum(self, nums: List[int]) -> List[int]:
        result = []
        running_sum = 0

        for num in nums:
            running_sum += num
            result.append(running_sum)
        return result
```

# 1456. Maximum Number of Vowels in a Substring of Given Length

```py
class Solution:
    def maxVowels(self, s: str, k: int) -> int:
        '''
        max = starts at 0
        vowels = list of vowels
        for from 0 to n - k
            length = starts at 0
            counter = starts at k
            While the current counter is greater than 0
                if the character is a vowel
                    increment the length
                decrement counter

                update the max
        return max

        Time Complexity: O(n * k)
        Space Complexity: O(1)

        Note: Since this is a Task 2 GCF simulation, it's okay to NOT provide the most efficient solution as they don't usually require it for this task.
        '''
        if len(s) <= 1:
            return len(s)
        max_length = 0
        n = len(s)
        vowels = ['a', 'e', 'i', 'o', 'u']
        for i in range(n - k + 1):
            curr_length = 0
            counter = k
            j = i
            while counter > 0:
                char = s[j]
                if char in vowels:
                    curr_length += 1
                counter -= 1
                j += 1
            max_length = max(max_length, curr_length)
        return max_length
```

# 560. Subarray Sum Equals K

```py
from collections import defaultdict
class Solution:
    def subarraySum(self, nums: List[int], k: int) -> int:
        '''
        intuitive approach:
            check every subarray
                get the sum of the subarray
                increment the max if a subarray sums up to k
        
        O(n) approach:
           0 [1, 2, 3]
              ^
            1. get a prefix sum of the sum that you've calculated
            2. initialize a hashmap to look up how many subarrays have summed up to k
            3. increment the counter if the prefix sum is found in the hashmap
        '''

        hashmap = defaultdict(int)
        hashmap[0] = 1
        prefix_sum = 0
        counter = 0
        for num in nums:
            prefix_sum += num
            complement = hashmap[prefix_sum - k]
            counter += complement
            hashmap[prefix_sum] += 1
        return counter
```
