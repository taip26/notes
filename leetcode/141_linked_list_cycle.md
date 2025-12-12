# 141. Linked List Cycle

## Strategy
Used fast/slow pointers and if they intersect, then there is a cycle
Setbacks
 - Check edge case where they are equal if both happen to reach the end of the list at the same time (both null)

## Solution
```python
class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        fast = head
        slow = head
        while fast is not None and slow is not None:
            fast = fast.next
            if fast is not None:
                fast = fast.next
            slow = slow.next
            if fast == slow and fast is not None:
                return True
        return False

```
