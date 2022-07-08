# Remove Nth Node From End of List
---
- ## Question:
> Given the head of a linked list, remove the nth node from the end of the list and return its head.
---
- ## Example:
![alt](https://assets.leetcode.com/uploads/2020/10/03/remove_ex1.jpg)
> Input: head = [1,2,3,4,5], n = 2
> 
> Output: [1,2,3,5]
---
- ## Solution:
**Code :**
```java
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode start=new ListNode(0);
        ListNode slow=start,fast=start;
        slow.next=head;
        for(int i=1;i<=n+1;i++)
        {
            fast=fast.next;
        }
        while(fast!=null)
        {
            slow=slow.next;
            fast=fast.next;
        }
        slow.next=slow.next.next;
        return start.next;
        
    }
}
