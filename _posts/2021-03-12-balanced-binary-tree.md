---
title: "Balanced Binary Tree"
date: 2021-03-12
categories: daily post
---
Balanced binary tree problem.
Determine if a tree is height balanced.

AVL tree is always height balanced.

Let's try a recursive solution. 
We will make a function called check().

check() function will return -1 if left or right is -1 or if left - right is bigger than 1. 

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isBalanced(self, root: TreeNode) -> bool:
        def check(root):
            if not root:
                return 0
            left = check(root.left)
            right = check(root.right)
            
            if left == -1 or right == -1 or abs(left - right) > 1:
                return -1
            return max(left, right) + 1
        
        return check(root) != -1
```
Time complexity O(n)
Space complexity O(n)