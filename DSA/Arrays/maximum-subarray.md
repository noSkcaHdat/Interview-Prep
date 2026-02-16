# Maximum Subarray (Kadane's Algorithm)

## Problem Statement

Given an integer array `nums`, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

## Source

- **Platform**: DSA/LeetCode
- **Difficulty**: Medium
- **Link**: https://leetcode.com/problems/maximum-subarray/

## Examples

### Example 1:
```
Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
Output: 6
Explanation: [4,-1,2,1] has the largest sum = 6.
```

### Example 2:
```
Input: nums = [1]
Output: 1
```

### Example 3:
```
Input: nums = [5,4,-1,7,8]
Output: 23
```

## Constraints

- 1 <= nums.length <= 10^5
- -10^4 <= nums[i] <= 10^4

## Approach

Use Kadane's algorithm to track the maximum sum ending at each position.

### Key Insights:
1. At each position, decide whether to extend the previous subarray or start a new one
2. If current sum becomes negative, it's better to start fresh
3. Keep track of global maximum throughout

### Algorithm:
1. Initialize max_sum and current_sum with first element
2. For each element starting from index 1:
   - Update current_sum = max(element, current_sum + element)
   - Update max_sum = max(max_sum, current_sum)
3. Return max_sum

## Complexity Analysis

- **Time Complexity**: O(n) - Single pass through the array
- **Space Complexity**: O(1) - Only using two variables

## Solution

### Python
```python
def maxSubArray(nums):
    """
    Find maximum subarray sum using Kadane's algorithm
    
    Time: O(n), Space: O(1)
    """
    max_sum = current_sum = nums[0]
    
    for num in nums[1:]:
        current_sum = max(num, current_sum + num)
        max_sum = max(max_sum, current_sum)
    
    return max_sum
```

### JavaScript
```javascript
function maxSubArray(nums) {
    let maxSum = nums[0];
    let currentSum = nums[0];
    
    for (let i = 1; i < nums.length; i++) {
        currentSum = Math.max(nums[i], currentSum + nums[i]);
        maxSum = Math.max(maxSum, currentSum);
    }
    
    return maxSum;
}
```

### Java
```java
class Solution {
    public int maxSubArray(int[] nums) {
        int maxSum = nums[0];
        int currentSum = nums[0];
        
        for (int i = 1; i < nums.length; i++) {
            currentSum = Math.max(nums[i], currentSum + nums[i]);
            maxSum = Math.max(maxSum, currentSum);
        }
        
        return maxSum;
    }
}
```

### C++
```cpp
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int maxSum = nums[0];
        int currentSum = nums[0];
        
        for (int i = 1; i < nums.size(); i++) {
            currentSum = max(nums[i], currentSum + nums[i]);
            maxSum = max(maxSum, currentSum);
        }
        
        return maxSum;
    }
};
```

## Related Problems

- Maximum Product Subarray
- Best Time to Buy and Sell Stock
- Longest Turbulent Subarray

## Tags

`array` `dynamic-programming` `divide-and-conquer` `kadane-algorithm`
