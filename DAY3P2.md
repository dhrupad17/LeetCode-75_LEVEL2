# Palindrome Linked List
---
- ## Question:
> Given the head of a singly linked list, return true if it is a palindrome.
---
- ## Example:
![alt](https://assets.leetcode.com/uploads/2021/03/03/pal1linked-list.jpg)
> Input: head = [1,2,2,1]
> 
> Output: true
---
- ## Solution:
**Code :**
```java
class Solution {
   public boolean isPalindrome(ListNode head) {
    ListNode fast = head, slow = head;
    while (fast != null && fast.next != null) {
        fast = fast.next.next;
        slow = slow.next;
    }
    if (fast != null) { // odd nodes: let right half smaller
        slow = slow.next;
    }
    slow = reverse(slow);
    fast = head;
    
    while (slow != null) {
        if (fast.val != slow.val) {
            return false;
        }
        fast = fast.next;
        slow = slow.next;
    }
    return true;
}

public ListNode reverse(ListNode head) {
    ListNode prev = null;
    while (head != null) {
        ListNode next = head.next;
        head.next = prev;
        prev = head;
        head = next;
    }
    return prev;
}
}
