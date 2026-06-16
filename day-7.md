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