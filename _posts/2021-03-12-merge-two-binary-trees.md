---
title: "Merge Two Binary Trees"
date: 2021-03-12
categories: daily post
---
Merge two binary trees problem.

Remember that a tree node is not just a node but a node with left and right relations.

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def mergeTrees(self, root1: TreeNode, root2: TreeNode) -> TreeNode:
        if root1 and root2:
            node = TreeNode(root1.val + root2.val)
            node.left = self.mergeTrees(root1.left, root2.left)
            node.right = self.mergeTrees(root1.right, root2.right)
            return node
        else:
            return root1 or root2
```
Time complexity O(n)
Space complexity O(n) and in a balanced case, O(logn)