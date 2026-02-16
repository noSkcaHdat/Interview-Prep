# Reverse Linked List

## Problem Statement

Given the head of a singly linked list, reverse the list and return the reversed list.

## Source

- **Platform**: DSA/LeetCode
- **Difficulty**: Easy
- **Link**: https://leetcode.com/problems/reverse-linked-list/

## Examples

### Example 1:
```
Input: head = [1,2,3,4,5]
Output: [5,4,3,2,1]
```

### Example 2:
```
Input: head = [1,2]
Output: [2,1]
```

### Example 3:
```
Input: head = []
Output: []
```

## Constraints

- The number of nodes in the list is in the range [0, 5000]
- -5000 <= Node.val <= 5000

## Approach

Use three pointers to reverse links in-place during single traversal.

### Key Insights:
1. Reverse pointer directions while traversing
2. Need to keep track of previous, current, and next nodes
3. Can be done iteratively or recursively

### Algorithm (Iterative):
1. Initialize prev = None, curr = head
2. While curr is not None:
   - Store next node
   - Reverse current node's pointer to prev
   - Move prev and curr one step forward
3. Return prev (new head)

## Complexity Analysis

- **Time Complexity**: O(n) - Single pass through the list
- **Space Complexity**: O(1) - Only using three pointers

## Solution

### Python
```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

def reverseList(head):
    """
    Reverse linked list iteratively
    
    Time: O(n), Space: O(1)
    """
    prev = None
    curr = head
    
    while curr:
        next_node = curr.next
        curr.next = prev
        prev = curr
        curr = next_node
    
    return prev
```

### JavaScript
```javascript
function reverseList(head) {
    let prev = null;
    let curr = head;
    
    while (curr !== null) {
        const nextNode = curr.next;
        curr.next = prev;
        prev = curr;
        curr = nextNode;
    }
    
    return prev;
}
```

### Java
```java
class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode prev = null;
        ListNode curr = head;
        
        while (curr != null) {
            ListNode nextNode = curr.next;
            curr.next = prev;
            prev = curr;
            curr = nextNode;
        }
        
        return prev;
    }
}
```

### C++
```cpp
class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        ListNode* prev = nullptr;
        ListNode* curr = head;
        
        while (curr != nullptr) {
            ListNode* nextNode = curr->next;
            curr->next = prev;
            prev = curr;
            curr = nextNode;
        }
        
        return prev;
    }
};
```

## Related Problems

- Reverse Linked List II
- Reverse Nodes in k-Group
- Palindrome Linked List

## Tags

`linked-list` `recursion` `iteration` `two-pointers`
