# Two Sum

## Problem Statement

Given an array of integers `nums` and an integer `target`, return indices of the two numbers such that they add up to `target`. You may assume that each input would have exactly one solution, and you may not use the same element twice.

## Source

- **Platform**: DSA/LeetCode
- **Difficulty**: Easy
- **Link**: https://leetcode.com/problems/two-sum/

## Examples

### Example 1:
```
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
```

### Example 2:
```
Input: nums = [3,2,4], target = 6
Output: [1,2]
```

### Example 3:
```
Input: nums = [3,3], target = 6
Output: [0,1]
```

## Constraints

- 2 <= nums.length <= 10^4
- -10^9 <= nums[i] <= 10^9
- -10^9 <= target <= 10^9
- Only one valid answer exists

## Approach

Use a hash map to store the complement of each element as we iterate through the array.

### Key Insights:
1. For each element `x`, we need to find if `target - x` exists in the array
2. Hash map provides O(1) lookup time
3. Single pass through array is sufficient

### Algorithm:
1. Create an empty hash map to store value -> index mapping
2. For each element in the array:
   - Calculate complement = target - current element
   - If complement exists in hash map, return [complement_index, current_index]
   - Otherwise, add current element to hash map
3. Return result

## Complexity Analysis

- **Time Complexity**: O(n) - Single pass through the array with O(1) hash map operations
- **Space Complexity**: O(n) - Hash map can store up to n elements

## Solution

### Python
```python
def twoSum(nums, target):
    """
    Find two indices that sum to target using hash map
    
    Time: O(n), Space: O(n)
    """
    seen = {}  # value -> index
    
    for i, num in enumerate(nums):
        complement = target - num
        if complement in seen:
            return [seen[complement], i]
        seen[num] = i
    
    return []  # No solution found
```

### JavaScript
```javascript
function twoSum(nums, target) {
    const seen = new Map();
    
    for (let i = 0; i < nums.length; i++) {
        const complement = target - nums[i];
        if (seen.has(complement)) {
            return [seen.get(complement), i];
        }
        seen.set(nums[i], i);
    }
    
    return [];
}
```

### Java
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> seen = new HashMap<>();
        
        for (int i = 0; i < nums.length; i++) {
            int complement = target - nums[i];
            if (seen.containsKey(complement)) {
                return new int[] { seen.get(complement), i };
            }
            seen.put(nums[i], i);
        }
        
        return new int[] {};
    }
}
```

### C++
```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int, int> seen;
        
        for (int i = 0; i < nums.size(); i++) {
            int complement = target - nums[i];
            if (seen.find(complement) != seen.end()) {
                return {seen[complement], i};
            }
            seen[nums[i]] = i;
        }
        
        return {};
    }
};
```

## Related Problems

- Three Sum
- Four Sum
- Two Sum II - Input Array Is Sorted

## Tags

`array` `hash-table` `two-pointers`
