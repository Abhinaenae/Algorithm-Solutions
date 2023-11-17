# 206. Reverse Linked List

Given the head of a singly linked list, reverse the list, and return the reversed list.


### Solution

Time Complexity: O(N)

Space Complexity: O(1)
```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        result = None
        current = head
        while current:
            nextnode = current.next
            current.next = result
            result = current
            current = nextnode
        return result
```
