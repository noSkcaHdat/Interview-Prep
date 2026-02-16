# Binary Tree Level Order Traversal

## Problem Statement

Given the root of a binary tree, return the level order traversal of its nodes' values (i.e., from left to right, level by level).

## Source

- **Platform**: DSA/LeetCode
- **Difficulty**: Medium
- **Link**: https://leetcode.com/problems/binary-tree-level-order-traversal/

## Examples

### Example 1:
```
Input: root = [3,9,20,null,null,15,7]
Output: [[3],[9,20],[15,7]]

Tree:
    3
   / \
  9  20
    /  \
   15   7
```

### Example 2:
```
Input: root = [1]
Output: [[1]]
```

### Example 3:
```
Input: root = []
Output: []
```

## Constraints

- The number of nodes in the tree is in the range [0, 2000]
- -1000 <= Node.val <= 1000

## Approach

Use BFS (Breadth-First Search) with a queue to traverse level by level.

### Key Insights:
1. Queue maintains nodes at current level
2. Process all nodes at one level before moving to next
3. Track level size to separate levels

### Algorithm:
1. If root is None, return empty list
2. Initialize queue with root and result list
3. While queue is not empty:
   - Get current level size
   - Create current level list
   - Process all nodes at this level
   - Add their children to queue
   - Add level list to result
4. Return result

## Complexity Analysis

- **Time Complexity**: O(n) - Visit each node exactly once
- **Space Complexity**: O(n) - Queue can hold up to n/2 nodes at bottom level

## Solution

### Python
```python
from collections import deque

class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def levelOrder(root):
    """
    Level order traversal using BFS
    
    Time: O(n), Space: O(n)
    """
    if not root:
        return []
    
    result = []
    queue = deque([root])
    
    while queue:
        level_size = len(queue)
        current_level = []
        
        for _ in range(level_size):
            node = queue.popleft()
            current_level.append(node.val)
            
            if node.left:
                queue.append(node.left)
            if node.right:
                queue.append(node.right)
        
        result.append(current_level)
    
    return result
```

### JavaScript
```javascript
function levelOrder(root) {
    if (!root) return [];
    
    const result = [];
    const queue = [root];
    
    while (queue.length > 0) {
        const levelSize = queue.length;
        const currentLevel = [];
        
        for (let i = 0; i < levelSize; i++) {
            const node = queue.shift();
            currentLevel.push(node.val);
            
            if (node.left) queue.push(node.left);
            if (node.right) queue.push(node.right);
        }
        
        result.push(currentLevel);
    }
    
    return result;
}
```

### Java
```java
class Solution {
    public List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> result = new ArrayList<>();
        if (root == null) return result;
        
        Queue<TreeNode> queue = new LinkedList<>();
        queue.offer(root);
        
        while (!queue.isEmpty()) {
            int levelSize = queue.size();
            List<Integer> currentLevel = new ArrayList<>();
            
            for (int i = 0; i < levelSize; i++) {
                TreeNode node = queue.poll();
                currentLevel.add(node.val);
                
                if (node.left != null) queue.offer(node.left);
                if (node.right != null) queue.offer(node.right);
            }
            
            result.add(currentLevel);
        }
        
        return result;
    }
}
```

## Related Problems

- Binary Tree Zigzag Level Order Traversal
- Binary Tree Right Side View
- Average of Levels in Binary Tree

## Tags

`tree` `binary-tree` `bfs` `queue` `breadth-first-search`
