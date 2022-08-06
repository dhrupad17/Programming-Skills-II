# Add Two Numbers
--- 
- ## Question:
> You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.
> 
> You may assume the two numbers do not contain any leading zero, except the number 0 itself.
---
- ## Example:
![ALT](https://assets.leetcode.com/uploads/2020/10/02/addtwonumber1.jpg)
> Input: l1 = [2,4,3], l2 = [5,6,4]
> 
> Output: [7,0,8]
> 
> Explanation: 342 + 465 = 807.
---
- ## Solution:
**Code :**
```java
class Solution {
    int carry=0;
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        if(l1==null && l2==null && carry==0)
            return null;
        int v1,v2;
        if(l1==null)
            v1=0;
        else
            v1=l1.val;
        if(l2==null)
            v2=0;
        else
            v2=l2.val;
        int sum=v1+v2+carry;
        carry=sum/10;
        if(l1==null)
            l1=null;
        else
            l1=l1.next;
        if(l2==null)
            l2=null;
        else
            l2=l2.next;
        ListNode ans=new ListNode(sum%10,addTwoNumbers(l1,l2));
        return ans;
    }
}
