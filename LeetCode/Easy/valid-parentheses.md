# Valid Parentheses

## Problem Statement

Given a string `s` containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

An input string is valid if:
1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.
3. Every close bracket has a corresponding open bracket of the same type.

## Source

- **Platform**: LeetCode
- **Difficulty**: Easy
- **Link**: https://leetcode.com/problems/valid-parentheses/

## Examples

### Example 1:
```
Input: s = "()"
Output: true
```

### Example 2:
```
Input: s = "()[]{}"
Output: true
```

### Example 3:
```
Input: s = "(]"
Output: false
```

## Constraints

- 1 <= s.length <= 10^4
- s consists of parentheses only '()[]{}'

## Approach

Use a stack to match opening and closing brackets.

### Key Insights:
1. Stack is perfect for matching pairs (LIFO structure)
2. Push opening brackets, pop and match on closing brackets
3. Valid string must have empty stack at the end

### Algorithm:
1. Create empty stack
2. For each character in string:
   - If opening bracket: push to stack
   - If closing bracket: check if stack top matches, then pop
   - If mismatch or empty stack: return false
3. Return true if stack is empty

## Complexity Analysis

- **Time Complexity**: O(n) - Single pass through the string
- **Space Complexity**: O(n) - Stack can hold up to n/2 elements

## Solution

### Python
```python
def isValid(s):
    """
    Check if parentheses are valid using stack
    
    Time: O(n), Space: O(n)
    """
    stack = []
    mapping = {')': '(', '}': '{', ']': '['}
    
    for char in s:
        if char in mapping:
            # Closing bracket
            top = stack.pop() if stack else '#'
            if mapping[char] != top:
                return False
        else:
            # Opening bracket
            stack.append(char)
    
    return len(stack) == 0
```

### JavaScript
```javascript
function isValid(s) {
    const stack = [];
    const mapping = {
        ')': '(',
        '}': '{',
        ']': '['
    };
    
    for (let char of s) {
        if (char in mapping) {
            const top = stack.length > 0 ? stack.pop() : '#';
            if (mapping[char] !== top) {
                return false;
            }
        } else {
            stack.push(char);
        }
    }
    
    return stack.length === 0;
}
```

### Java
```java
class Solution {
    public boolean isValid(String s) {
        Stack<Character> stack = new Stack<>();
        Map<Character, Character> mapping = new HashMap<>();
        mapping.put(')', '(');
        mapping.put('}', '{');
        mapping.put(']', '[');
        
        for (char c : s.toCharArray()) {
            if (mapping.containsKey(c)) {
                char top = stack.isEmpty() ? '#' : stack.pop();
                if (mapping.get(c) != top) {
                    return false;
                }
            } else {
                stack.push(c);
            }
        }
        
        return stack.isEmpty();
    }
}
```

## Related Problems

- Generate Parentheses
- Longest Valid Parentheses
- Remove Invalid Parentheses

## Tags

`string` `stack` `parentheses`
