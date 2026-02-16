# First Negative in Every Window

## Problem Statement

Given an array and a positive integer k, find the first negative integer for each window of size k. If a window does not contain a negative integer, output 0 for that window.

## Source

- **Platform**: GeeksforGeeks
- **Difficulty**: Easy
- **Link**: https://practice.geeksforgeeks.org/problems/first-negative-integer-in-every-window-of-size-k/

## Examples

### Example 1:
```
Input: arr[] = [-8, 2, 3, -6, 10], k = 2
Output: [-8, 0, -6, -6]
Explanation:
Window 1: [-8, 2] → first negative is -8
Window 2: [2, 3] → no negative, output 0
Window 3: [3, -6] → first negative is -6
Window 4: [-6, 10] → first negative is -6
```

### Example 2:
```
Input: arr[] = [12, -1, -7, 8, -15, 30, 16, 28], k = 3
Output: [-1, -1, -7, -15, -15, 0]
```

## Constraints

- 1 <= k <= arr.length <= 10^5
- -10^5 <= arr[i] <= 10^5

## Approach

Use sliding window with queue to efficiently track negative numbers.

### Key Insights:
1. Use deque to store indices of negative numbers in current window
2. Front of deque always has the first negative in window
3. Remove indices that fall outside current window

### Algorithm:
1. Create empty deque and result list
2. Process first k elements, store negative indices in deque
3. Add first negative (or 0) to result
4. For remaining elements:
   - Remove indices outside current window from deque front
   - Add current element if negative
   - Add first negative (or 0) to result
5. Return result

## Complexity Analysis

- **Time Complexity**: O(n) - Each element added and removed from deque at most once
- **Space Complexity**: O(k) - Deque can store at most k elements

## Solution

### Python
```python
def firstNegative(arr, k):
    """
    Find first negative integer in every window of size k
    
    Time: O(n), Space: O(k)
    """
    from collections import deque
    
    dq = deque()
    result = []
    
    # Process first window
    for i in range(k):
        if arr[i] < 0:
            dq.append(i)
    
    # First window result
    if dq:
        result.append(arr[dq[0]])
    else:
        result.append(0)
    
    # Process remaining windows
    for i in range(k, len(arr)):
        # Remove elements outside window
        while dq and dq[0] <= i - k:
            dq.popleft()
        
        # Add current if negative
        if arr[i] < 0:
            dq.append(i)
        
        # Add result for current window
        if dq:
            result.append(arr[dq[0]])
        else:
            result.append(0)
    
    return result
```

### JavaScript
```javascript
function firstNegative(arr, k) {
    const dq = [];
    const result = [];
    
    // Process first window
    for (let i = 0; i < k; i++) {
        if (arr[i] < 0) {
            dq.push(i);
        }
    }
    
    // First window result
    result.push(dq.length > 0 ? arr[dq[0]] : 0);
    
    // Process remaining windows
    for (let i = k; i < arr.length; i++) {
        // Remove elements outside window
        while (dq.length > 0 && dq[0] <= i - k) {
            dq.shift();
        }
        
        // Add current if negative
        if (arr[i] < 0) {
            dq.push(i);
        }
        
        // Add result for current window
        result.push(dq.length > 0 ? arr[dq[0]] : 0);
    }
    
    return result;
}
```

### Java
```java
class Solution {
    public long[] firstNegative(long[] arr, int k) {
        Deque<Integer> dq = new LinkedList<>();
        long[] result = new long[arr.length - k + 1];
        int idx = 0;
        
        // Process first window
        for (int i = 0; i < k; i++) {
            if (arr[i] < 0) {
                dq.addLast(i);
            }
        }
        
        // First window result
        result[idx++] = dq.isEmpty() ? 0 : arr[dq.peekFirst()];
        
        // Process remaining windows
        for (int i = k; i < arr.length; i++) {
            // Remove elements outside window
            while (!dq.isEmpty() && dq.peekFirst() <= i - k) {
                dq.removeFirst();
            }
            
            // Add current if negative
            if (arr[i] < 0) {
                dq.addLast(i);
            }
            
            // Add result for current window
            result[idx++] = dq.isEmpty() ? 0 : arr[dq.peekFirst()];
        }
        
        return result;
    }
}
```

## Related Problems

- Sliding Window Maximum
- Max of Min for Every Window Size
- Count Distinct Elements in Window

## Tags

`array` `sliding-window` `queue` `deque`
