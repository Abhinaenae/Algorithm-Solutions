# 875. Middle of the Linked List

Given the head of a singly linked list, return the middle node of the linked list.

If there are two middle nodes, return the second middle node.

## Solution

I have two solutions for this. 
The first is the brute force solution, running in 2*O(n).

### Brute Force: 
Time Complexity: O(n) + O(n) = 2*O(n)

Space Complexity: O(1)

The steps I took for this were to count the number of nodes in the linked list using a count variable, and then loop through the linked list again for count/2 iterations.
```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def middleNode(self, head: Optional[ListNode]) -> Optional[ListNode]:
        count = 0
        current = head
        while(current != None):
            count += 1
            current = current.next
        current = head
        for i in range(int(count/2)):
            current = current.next
        return current
```

### Optimized: 
Time Complexity: O(n/2)

Space Complexity: O(1)

I used a two-pointer approach, letting me go through only half the size of the linked list.
```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def middleNode(self, head: Optional[ListNode]) -> Optional[ListNode]:
        current = head
        curr2 = head
        while(curr2 != None and curr2.next != None):
            current = current.next
            curr2 = curr2.next.next
        return current
        
```
