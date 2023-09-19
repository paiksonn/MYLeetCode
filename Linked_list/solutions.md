- __EASY__ Reverse Linked List [link](https://leetcode.com/problems/reverse-linked-list/?envType=study-plan-v2&envId=leetcode-75)
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def reverseList(self, head):
        prev = None
        curr = head
        while curr:
            next = curr.next
            curr.next = prev
            prev = curr
            curr = next
        return prev     
```

- __MEDIUM__ Delete the Middle Node of a Linked List [link](https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/?envType=study-plan-v2&envId=leetcode-75)
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def deleteMiddle(self, head: Optional[ListNode]) -> Optional[ListNode]:  
        if not head.next:
            return head.next
        fast, slow = head.next.next, head
        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next
        slow.next = slow.next.next
        return head
```

