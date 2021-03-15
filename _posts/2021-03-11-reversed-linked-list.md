---
title: "Reverse Linked List"
date: 2021-03-11
categories: daily post
---
Reverse linked list problem has both a recursive solution and an iterative solution.

First, let's look at the recursive solution.
In recursive solution we will have a reverse(currentNode, prevNode) function. What the reverse function does is, it will start from the first node and keep moving down to the last node. 

For example, in a linked list 1->2->3->4->5->None
reverse(1, None) will do None<-1 and return reverse(2, 1).
reverse(2, 1) will do 1<-2, which will result in None<-1<-2 and return reverse(3, 2).
reverse(3, 2) will do the reverse and return reverse(4, 3).
reverse(4, 3) will return reverse(5, 4) and reverse(5, 4) will return reverse(None, 5).

When currentNode is None, we have reached the base case. So for reverse(None, 5), we will
return node 5, which is connected to other nodes like this.
5->4->3->2->1->None
Then, we will move up the recursive call stack and get to reverse(1, None) which will return 5->4->3->2->1->None. 

This solution has O(n) time and O(n) space complexity where n is the number of nodes in the linked list. 

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseList(self, head: ListNode) -> ListNode:
        def reverse(currentNode: ListNode, prevNode: ListNode = None):
            if not currentNode:
                return prevNode
            
            nextNode = currentNode.next
            currentNode.next = prevNode
            return reverse(nextNode, currentNode)
        return reverse(head)
```
Iterative solution is very similar but it uses a while loop and manually moves prevNode to currentNode and currentNode to nextNode. 
Iterative solution has O(n) time and O(1) space complexity.

```python
class Solution:
    def reverseList(self, head: ListNode) -> ListNode:
        currentNode, prevNode = head, None
        
        while currentNode:
            nextNode = currentNode.next
            currentNode.next = prevNode
            
            prevNode = currentNode
            currentNode = nextNode
            
        return prevNode
```