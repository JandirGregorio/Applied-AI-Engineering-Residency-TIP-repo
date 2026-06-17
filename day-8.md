# Day 8 

## 128. Longest Consecutive Sequence

```py
class Solution:
    def longestConsecutive(self, nums: List[int]) -> int:
        '''
        convert the array nums into a set so we can have O(1) look up time
        variable to keep track of the longest sequence
        iterate through the array
            verify if the current number we're traversing through is the start of the sequence
                if it is 
                    then initialize the counter to 1
                    check if num + counter exists in the set
                        increment counter by 1
                    get the max between the counter and longest so we keep track of the longest sequence
                otherwise
                    set back to zero
        return longest sequence
        
        '''
        num_set = set(nums)
        longest = 0
        for num in nums:
            if num - 1 not in num_set:
                currLength = 1
                while (num + currLength) in num_set:
                    currLength += 1
                longest = longest if longest > currLength else currLength
        return longest
```

Notes: passing 81/85 in Leetcode. `nums` was too large and my algorithm exceeded run time. First I was using `max` thinking it was messing with the algorithm so I used a conditional statement. However, the real problem is the while loop that's iterating through `num_set` again.

Update: the problem was that I was iterating through the `nums` array itself. This means that I was checking duplicates several times and could take O(n^2) iterations in the worst case scenario. Instead, I iterated through the set and passed all the tests. This removed duplicate work and improved efficiency.
