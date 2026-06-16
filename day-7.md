# Day 7 Top K frequent elements
```py
from collections import Counter
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        '''
        create a counter for the frequency of each number


        go through the array to k
            find the max value in the dictionary
            store the value in the result
            delete the key
            decrease k

        time complexity: O(n * k) -> while loop iterating through k (O(k)) and max (O(n))
        space complexity: O(n) -> dictionary
        '''
        frequency = Counter(nums)
        most_frequent = []
        while k > 0:
            maxKey = max(frequency, key=frequency.get)
            most_frequent.append(maxKey)
            del frequency[maxKey]
            k -= 1
        return most_frequent
```

## Bucket sort solution
1. Create counter
2. Since we know that there will be maximum n elements that repeat, we can create a matrix to hold the frequency where the index represents how many times each ele shows up and the element is the actual element
3. since the most frequent element will the at the last index of the array, then reverse traverse the array and append the elements to the result array until we the length of the result is the same as k
```py
class solution:
  def topKFrequent(self, nums: List[int], k: int) -> List[int]:
    counter = {}
    bucket = [[] for i in range(len(nums) + 1)]
    
    for num in nums:
      counter[num] = counter.get(num, 0) + 1
    
    for val, count in counter.items():
      bucket[count].append(val)

    result = []
    for i in range(len(bucket) - 1, 0, -1):
      for num in bucket[i]:
        result.append(num)
          if k == len(result):
            return result
```