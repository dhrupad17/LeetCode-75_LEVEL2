# Odd Even Linked List
---
- ## Question:
> Given the head of a singly linked list, group all the nodes with odd indices together followed by the nodes with even indices, and return the reordered list.
> 
> The first node is considered odd, and the second node is even, and so on.
> 
> Note that the relative order inside both the even and odd groups should remain as it was in the input.
> 
> You must solve the problem in O(1) extra space complexity and O(n) time complexity.
---
- ## Example:
![alt](https://assets.leetcode.com/uploads/2021/03/10/oddeven-linked-list.jpg)
> Input: head = [1,2,3,4,5]
> 
> Output: [1,3,5,2,4]
---
- ## Solution:
**Code :**
```java
class Solution {
    public ListNode oddEvenList(ListNode head) {
        if(head!=null)
        {
            ListNode odd=head,even=head.next,evenHead=even;
            while(even!=null && even.next !=null)
            {
                odd.next=odd.next.next;
                even.next=even.next.next;
                odd=odd.next;
                even=even.next;
            }
            odd.next=evenHead;
        }
        return head;
    }
}
