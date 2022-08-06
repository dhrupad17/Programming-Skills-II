# Add Two Numbers II
--- 
- ## Question:
> You are given two non-empty linked lists representing two non-negative integers. The most significant digit comes first and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.
> 
> You may assume the two numbers do not contain any leading zero, except the number 0 itself.
---
- ## Example:
![ALT](https://assets.leetcode.com/uploads/2021/04/09/sumii-linked-list.jpg)
> Input: l1 = [7,2,4,3], l2 = [5,6,4]
> 
> Output: [7,8,0,7]
---
- ## Solution:
**Code :**
```java
class Solution {
    ListNode reverse(ListNode s){
        ListNode ans = null;
        
        while(s != null){
            ans = new ListNode(s.val, ans);
            s = s.next;
        }
        return ans;
    }
    ListNode add(ListNode l1,ListNode l2)
    {
        int sum=0;
        int carry=0;
        ListNode temp=new ListNode(0);
        ListNode ans=temp;
        while(l1!=null || l2!=null || carry!=0)
        {
            sum=0;
            if(l1!=null)
            {
                sum=sum+l1.val;
                l1=l1.next;
            }
            if(l2!=null)
            {
                sum=sum+l2.val;
                l2=l2.next;
            }
            sum=sum+carry;
            carry=sum/10;
            ListNode x=new ListNode(sum%10);
            temp.next=x;
            temp=temp.next;
        }
        return ans.next;
    }
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode one = reverse(l1);
        ListNode two = reverse(l2);
        
        ListNode ans = add(one, two);
        
        return reverse(ans);
    }
}
