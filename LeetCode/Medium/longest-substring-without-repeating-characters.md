# Longest Substring Without Repeating Characters

## Problem Statement

Given a string `s`, find the length of the longest substring without repeating characters.

## Source

- **Platform**: LeetCode
- **Difficulty**: Medium
- **Link**: https://leetcode.com/problems/longest-substring-without-repeating-characters/

## Examples

### Example 1:
```
Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.
```

### Example 2:
```
Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```

### Example 3:
```
Input: s = "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
```

## Constraints

- 0 <= s.length <= 5 * 10^4
- s consists of English letters, digits, symbols and spaces

## Approach

Use sliding window technique with hash set to track unique characters.

### Key Insights:
1. Sliding window maintains a substring without duplicates
2. Expand window by moving right pointer
3. Shrink window from left when duplicate is found
4. Track maximum window size

### Algorithm:
1. Initialize left pointer, max_length, and character set
2. For each right pointer position:
   - While character at right is in set, remove left character and move left pointer
   - Add right character to set
   - Update max_length
3. Return max_length

## Complexity Analysis

- **Time Complexity**: O(n) - Each character visited at most twice (once by right, once by left)
- **Space Complexity**: O(min(n, m)) - where m is character set size (128 for ASCII)

## Solution

### Python
```python
def lengthOfLongestSubstring(s):
    """
    Find longest substring without repeating characters using sliding window
    
    Time: O(n), Space: O(min(n, m))
    """
    char_set = set()
    left = 0
    max_length = 0
    
    for right in range(len(s)):
        while s[right] in char_set:
            char_set.remove(s[left])
            left += 1
        
        char_set.add(s[right])
        max_length = max(max_length, right - left + 1)
    
    return max_length
```

### JavaScript
```javascript
function lengthOfLongestSubstring(s) {
    const charSet = new Set();
    let left = 0;
    let maxLength = 0;
    
    for (let right = 0; right < s.length; right++) {
        while (charSet.has(s[right])) {
            charSet.delete(s[left]);
            left++;
        }
        
        charSet.add(s[right]);
        maxLength = Math.max(maxLength, right - left + 1);
    }
    
    return maxLength;
}
```

### Java
```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        Set<Character> charSet = new HashSet<>();
        int left = 0;
        int maxLength = 0;
        
        for (int right = 0; right < s.length(); right++) {
            while (charSet.contains(s.charAt(right))) {
                charSet.remove(s.charAt(left));
                left++;
            }
            
            charSet.add(s.charAt(right));
            maxLength = Math.max(maxLength, right - left + 1);
        }
        
        return maxLength;
    }
}
```

## Related Problems

- Longest Substring with At Most Two Distinct Characters
- Longest Substring with At Most K Distinct Characters
- Substring with Concatenation of All Words

## Tags

`string` `sliding-window` `hash-table` `two-pointers`
