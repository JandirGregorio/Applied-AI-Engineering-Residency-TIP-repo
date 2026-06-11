# Day 3

## Reverse String -- JavaScript Solution:

```js
function reverseString(s) {
  let left = 0;
  let right = s.length - 1;
  while (left < right) {
    let temp = s[left];
    s[left] = s[right];
    s[right] = temp;
    left++;
    right--;
  }
  return s;
}
```

### What it does

This algorithm uses a two-pointer approach to reverse a string. One pointer starts at the beginning and the other one starts at the end to swap the values.

```py
class Solution:
    def reverseString(self, s: List[str]) -> None:
        left = 0
        right = len(s) - 1

        while (left < right):
            temp = s[left]
            s[left] = s[right]
            s[right] = temp
            left += 1
            right -= 1
        return s
```

## Longest Substring Without Repeating Characters -- JavaScript Solution:

```js
function lengthOfLongestSubstring(s) {
  let seen = {};
  let left = 0;
  let maxLength = 0;
  for (let right = 0; right < s.length; right++) {
    if (seen[s[right]] !== undefined && seen[s[right]] >= left) {
      left = seen[s[right]] + 1;
    }
    seen[s[right]] = right;
    maxLength = Math.max(maxLength, right - left + 1);
  }
  return maxLength;
}
```

### What it does

It uses a slide window approach across the string, shrinking from the left whenever a duplicate character is found. It tracks the longest window seen throughout the process and returns it.

```py
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        seen = {}
        left = 0
        maxLength = 0
        for right in range(len(s)):
            if s[right] in seen and seen[s[right]] >= left:
                left = seen[s[right]] + 1
            seen[s[right]] = right
            maxLength = max(maxLength, right - left + 1)
        return maxLength
```

