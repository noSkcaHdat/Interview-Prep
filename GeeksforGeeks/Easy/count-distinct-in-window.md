# Count Distinct Elements in Every Window

## Problem Statement

Given an array of integers and a number k, find the count of distinct elements in every window of size k in the array.

## Source

- **Platform**: GeeksforGeeks
- **Difficulty**: Easy
- **Link**: https://practice.geeksforgeeks.org/problems/count-distinct-elements-in-every-window/

## Examples

### Example 1:
```
Input: arr[] = [1, 2, 1, 3, 4, 2, 3], k = 4
Output: [3, 4, 4, 3]
Explanation: 
Window 1: [1, 2, 1, 3] - distinct elements: 1, 2, 3 (count = 3)
Window 2: [2, 1, 3, 4] - distinct elements: 1, 2, 3, 4 (count = 4)
Window 3: [1, 3, 4, 2] - distinct elements: 1, 2, 3, 4 (count = 4)
Window 4: [3, 4, 2, 3] - distinct elements: 2, 3, 4 (count = 3)
```

### Example 2:
```
Input: arr[] = [1, 2, 4, 4], k = 2
Output: [2, 2, 1]
```

## Constraints

- 1 <= k <= arr.length <= 10^5
- 1 <= arr[i] <= 10^5

## Approach

Use sliding window with hash map to track element frequencies in current window.

### Key Insights:
1. Maintain a frequency map for current window
2. Size of map gives count of distinct elements
3. Slide window: remove leftmost, add rightmost element

### Algorithm:
1. Create frequency map for first k elements
2. Add size of map to result
3. For remaining elements:
   - Remove leftmost element from window (decrement/remove from map)
   - Add new rightmost element (increment in map)
   - Add current map size to result
4. Return result array

## Complexity Analysis

- **Time Complexity**: O(n) - Single pass through array with O(1) hash operations
- **Space Complexity**: O(k) - Hash map stores at most k distinct elements

## Solution

### Python
```python
def countDistinct(arr, k):
    """
    Count distinct elements in every window of size k
    
    Time: O(n), Space: O(k)
    """
    from collections import defaultdict
    
    freq = defaultdict(int)
    result = []
    
    # First window
    for i in range(k):
        freq[arr[i]] += 1
    result.append(len(freq))
    
    # Slide window
    for i in range(k, len(arr)):
        # Remove leftmost element
        freq[arr[i - k]] -= 1
        if freq[arr[i - k]] == 0:
            del freq[arr[i - k]]
        
        # Add rightmost element
        freq[arr[i]] += 1
        
        result.append(len(freq))
    
    return result
```

### JavaScript
```javascript
function countDistinct(arr, k) {
    const freq = new Map();
    const result = [];
    
    // First window
    for (let i = 0; i < k; i++) {
        freq.set(arr[i], (freq.get(arr[i]) || 0) + 1);
    }
    result.push(freq.size);
    
    // Slide window
    for (let i = k; i < arr.length; i++) {
        // Remove leftmost element
        const leftElem = arr[i - k];
        freq.set(leftElem, freq.get(leftElem) - 1);
        if (freq.get(leftElem) === 0) {
            freq.delete(leftElem);
        }
        
        // Add rightmost element
        freq.set(arr[i], (freq.get(arr[i]) || 0) + 1);
        
        result.push(freq.size);
    }
    
    return result;
}
```

### Java
```java
class Solution {
    public ArrayList<Integer> countDistinct(int[] arr, int k) {
        HashMap<Integer, Integer> freq = new HashMap<>();
        ArrayList<Integer> result = new ArrayList<>();
        
        // First window
        for (int i = 0; i < k; i++) {
            freq.put(arr[i], freq.getOrDefault(arr[i], 0) + 1);
        }
        result.add(freq.size());
        
        // Slide window
        for (int i = k; i < arr.length; i++) {
            // Remove leftmost element
            int leftElem = arr[i - k];
            freq.put(leftElem, freq.get(leftElem) - 1);
            if (freq.get(leftElem) == 0) {
                freq.remove(leftElem);
            }
            
            // Add rightmost element
            freq.put(arr[i], freq.getOrDefault(arr[i], 0) + 1);
            
            result.add(freq.size());
        }
        
        return result;
    }
}
```

## Related Problems

- Sliding Window Maximum
- Find All Anagrams in a String
- Longest Substring Without Repeating Characters

## Tags

`array` `sliding-window` `hash-table` `counting`
