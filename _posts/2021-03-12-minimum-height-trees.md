---
title: "Minimum Height Trees"
date: 2021-03-12
categories: daily post
---
Minimum height trees problem.

In order to have the minimum height tree, the node that is in the very middle 
should be the root node. This means, if we delete leaf nodes until we get to the
very center, we can find the root node that will make the tree have minimum height. 
```python
class Solution:
    def findMinHeightTrees(self, n: int, edges: List[List[int]]) -> List[int]:
        if n <= 1:
            return [0]
        
        # Form an undirected graph
        graph = collections.defaultdict(list)
        for i, j in edges:
            graph[i].append(j)
            graph[j].append(i)
            
        # Find first group of leaves
        leaves = []
        for i in range(n):
            if len(graph[i]) == 1:
                leaves.append(i)
                
        while n > 2:
            n-= len(leaves)
            new_leaves = []
            for leaf in leaves:
                neighbor = graph[leaf].pop()
                graph[neighbor].remove(leaf)
                
                if len(graph[neighbor]) == 1:
                    new_leaves.append(neighbor)
                    
            leaves = new_leaves
        return leaves
```

Time complexity O(n)
Space complexity O(n)