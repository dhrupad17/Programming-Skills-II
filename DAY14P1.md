# Reorder List
--- 
- ## Question:
> You are given the head of a singly linked-list. The list can be represented as:
> 
> L0 → L1 → … → Ln - 1 → Ln
> 
> Reorder the list to be on the following form:
> 
> L0 → Ln → L1 → Ln - 1 → L2 → Ln - 2 →
> 
> You may not modify the values in the list's nodes. Only nodes themselves may be changed.
---
- ## Example:
![alt](https://assets.leetcode.com/uploads/2021/03/04/reorder1linked-list.jpg)
> Input: head = [1,2,3,4]
> 
> Output: [1,4,2,3]
---
- ## Solution:
**Code :**
```java
class Solution {
    public void reorderList(ListNode head) {
        ListNode fast=head.next;
        ListNode slow=head;
        while(fast!=null && fast.next!=null)
        {
            slow=slow.next;
            fast=fast.next.next;
        }
        ListNode second=slow.next;
        ListNode prev=slow.next=null;
        while(second!=null)
        {
            ListNode temp=second.next;
            second.next=prev;
            prev=second;
            second=temp;
        }
        ListNode temp1=head;
        ListNode temp2=prev;
        while(temp2!=null)
        {
            temp1=temp1.next;
            temp2=temp2.next;
            head.next=prev;
            prev.next=temp1;
            head=temp1;
            prev=temp2;
        }
    }
}
