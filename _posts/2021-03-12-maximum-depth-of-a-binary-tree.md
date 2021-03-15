---
title: "Maximum Depth of a Binary Tree"
date: 2021-03-12
categories: daily post
---
Maximum depth of binary tree problem.
We can use BFS to solve this problem.
Queue can be used for BFS.

List can be used to create queue. But if we use deque in python, we can use it as a 
double linked list and each side can be popped in O(1) time. 
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def maxDepth(self, root: TreeNode) -> int:
        if root is None:
            return 0
        queue = collections.deque([root])
        depth = 0
        
        while queue:
            depth += 1
            for _ in range(len(queue)):
                cur_root = queue.popleft()
                if cur_root.left:
                    queue.append(cur_root.left)
                if cur_root.right:
                    queue.append(cur_root.right)
        return depth
```
Time complexity is O(n).
Space complexity is O(n) since in worst case, we need to hold all nodes in the queue.