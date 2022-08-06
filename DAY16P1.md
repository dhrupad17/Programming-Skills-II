# Rotate List
--- 
- ## Question:
> Given the head of a linked list, rotate the list to the right by k places.
---
- ## Example:
![ALT](https://assets.leetcode.com/uploads/2020/11/13/rotate1.jpg)
> Input: head = [1,2,3,4,5], k = 2
> 
> Output: [4,5,1,2,3]
---
- ## Solution:
**Code :**
```java
class Solution {
    public ListNode rotateRight(ListNode head, int k) {
        if(head==null||k==0)
            return head;
        ListNode p=head;
        int len=1;
        while(p.next!=null)
        {
            p=p.next;
            len++;
        }
        p.next=head;
        k=k%len;
        for(int i=0;i<len-k;i++)
        {
            p=p.next;
        }
        head=p.next;
        p.next=null;
        return head;
    }
}
