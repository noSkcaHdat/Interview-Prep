# Array Stabilization

## Problem Statement

You are given an array of n integers. In one operation, you can remove either the maximum or minimum element from the array. Find the minimum number of operations required to make all remaining elements equal.

## Source

- **Platform**: Codeforces
- **Difficulty**: Div 2 - A/B
- **Link**: Codeforces Problem

## Examples

### Example 1:
```
Input: n = 3, arr = [1, 3, 2]
Output: 1
Explanation: Remove the maximum (3), leaving [1, 2]. Then remove max (2), leaving [1, 1]. Total = 2 operations.
Or remove minimum (1), leaving [3, 2]. Then remove min (2), leaving [3, 3]. Total = 2 operations.
Actually, best is to keep the element with highest frequency.
```

### Example 2:
```
Input: n = 4, arr = [1, 2, 3, 4]
Output: 3
Explanation: All elements are unique, so we need to remove n-1 = 3 elements to make all remaining equal.
Keep any one element (e.g., keep 2), remove the other 3 elements.
```

### Example 3:
```
Input: n = 5, arr = [5, 5, 5, 5, 5]
Output: 0
Explanation: All elements already equal
```

## Constraints

- 1 <= n <= 10^5
- 1 <= arr[i] <= 10^9

## Approach

The key insight is that we need to keep only one unique value. We should keep the value that requires minimum removals.

### Key Insights:
1. Final array must have all equal elements
2. Count frequency of each unique element
3. We can only remove min/max, so simulate the process
4. Optimal: keep the most frequent element

### Algorithm:
1. If all elements already equal, return 0
2. Count unique elements
3. For each possible final value, count operations needed
4. Return minimum operations

## Complexity Analysis

- **Time Complexity**: O(n) - Linear scan to find unique elements and count
- **Space Complexity**: O(n) - Hash map for frequency counting

## Solution

### Python
```python
def minOperations(arr):
    """
    Find minimum operations to make all elements equal
    
    Time: O(n), Space: O(n)
    """
    from collections import Counter
    
    n = len(arr)
    
    # If all equal already
    if len(set(arr)) == 1:
        return 0
    
    # Count frequencies
    freq = Counter(arr)
    
    # Maximum frequency
    max_freq = max(freq.values())
    
    # Minimum removals = n - max_freq
    return n - max_freq
```

### JavaScript
```javascript
function minOperations(arr) {
    const n = arr.length;
    
    // If all equal already
    const uniqueSet = new Set(arr);
    if (uniqueSet.size === 1) {
        return 0;
    }
    
    // Count frequencies
    const freq = new Map();
    for (let num of arr) {
        freq.set(num, (freq.get(num) || 0) + 1);
    }
    
    // Maximum frequency
    let maxFreq = 0;
    for (let count of freq.values()) {
        maxFreq = Math.max(maxFreq, count);
    }
    
    // Minimum removals
    return n - maxFreq;
}
```

### Java
```java
class Solution {
    public int minOperations(int[] arr) {
        int n = arr.length;
        
        // Count frequencies
        Map<Integer, Integer> freq = new HashMap<>();
        for (int num : arr) {
            freq.put(num, freq.getOrDefault(num, 0) + 1);
        }
        
        // If all equal already
        if (freq.size() == 1) {
            return 0;
        }
        
        // Maximum frequency
        int maxFreq = 0;
        for (int count : freq.values()) {
            maxFreq = Math.max(maxFreq, count);
        }
        
        // Minimum removals
        return n - maxFreq;
    }
}
```

### C++
```cpp
class Solution {
public:
    int minOperations(vector<int>& arr) {
        int n = arr.size();
        
        // Count frequencies
        unordered_map<int, int> freq;
        for (int num : arr) {
            freq[num]++;
        }
        
        // If all equal already
        if (freq.size() == 1) {
            return 0;
        }
        
        // Maximum frequency
        int maxFreq = 0;
        for (auto& p : freq) {
            maxFreq = max(maxFreq, p.second);
        }
        
        // Minimum removals
        return n - maxFreq;
    }
};
```

## Related Problems

- Make Array Elements Equal
- Minimum Deletions to Make Array Beautiful
- Equal Sum Arrays With Minimum Number of Operations

## Tags

`array` `greedy` `hash-table` `counting`
