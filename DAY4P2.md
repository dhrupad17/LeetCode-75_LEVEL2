# Sort List
---
- ## Question:
> Given the head of a linked list, return the list after sorting it in ascending order.
---
- ## Example:
![ALT](https://assets.leetcode.com/uploads/2020/09/14/sort_list_1.jpg)
> Input: head = [4,2,1,3]
> 
> Output: [1,2,3,4]
---
- ## Solution:
**Code :**
```java
class Solution {
    public ListNode sortList(ListNode head) {
        if(head==null||head.next==null)
            return head;
        ListNode prev=head,slow=head,fast=head;
        while(fast!=null && fast.next!=null)
        {
            prev=slow;
            slow=slow.next;
            fast=fast.next.next;
        }
        prev.next=null;
        return merge(sortList(head),sortList(slow));
    }
    public ListNode merge(ListNode l1, ListNode l2) {
    if(l1 == null) return l2;
    if(l2 == null) return l1;
    if(l1.val <= l2.val) {
        l1.next = merge(l1.next, l2);
        return l1;
    } else {
        l2.next = merge(l1, l2.next);
        return l2;
    }
}
}
