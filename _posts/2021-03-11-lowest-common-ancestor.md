---
title: "Lowest Common Ancestor"
date: 2021-03-11
categories: daily post
---
Lowest Common Ancestor Problem.

What is lowest common ancestor?
Lowest common ancestor can be thought of as the first ancestor where two nodes meet.

If the values for two nodes are given, we should first find where those two nodes are in the tree.
This will take O(n) where n is the number of nodes in the tree, assuming that tree is not sorted.

To solve this problem, we can try defining a path_to_x(node, x) function. 
This function will return the path to x from the node position. 
If we can find the two paths for two nodes and compare the common parts of those two paths,
the last item in that common part would be the lowest common ancestor. 

Using this method, the overall time complexity will be O(n).
Auxiliary space complexity will be O(logn), assuming that the tree is balanced.

We can write this path_to_x(node, x) function recursively. 
For recursive solutions, we first need to find the base cases. 
the base case will be when the node is null or node's value == x.

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
        path_to_p = self.path_to_x(root, p)
        path_to_q = self.path_to_x(root, q)
        
        if not path_to_p or not path_to_q:
            return None
        
        LCA = None
        
        while path_to_p and path_to_q:
            pathElementToP = path_to_p.pop()
            pathElementToQ = path_to_q.pop()
            if pathElementToP.val == pathElementToQ.val:
                LCA = pathElementToP
            else:
                return LCA
        return LCA
        
        
    
    
    def path_to_x(self, root, x):
        if not root:
            return None
        if root.val == x.val:
            stack = []
            stack.append(root)
            return stack
        
        leftPath = self.path_to_x(root.left, x)
        rightPath = self.path_to_x(root.right, x)
        
        if leftPath:
            leftPath.append(root)
            return leftPath
        
        if rightPath:
            rightPath.append(root)
            return rightPath
```
[LeetCode 236]

[LeetCode 236]: https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/
