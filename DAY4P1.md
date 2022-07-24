# Linked List in Binary Tree
--- 
- ## Question:
> Given a binary tree root and a linked list with head as the first node. 
> 
> Return True if all the elements in the linked list starting from the head correspond to some downward path connected in the binary tree otherwise return False.
> 
> In this context downward path means a path that starts at some node and goes downwards.
---
- ## Example:
![alt](https://assets.leetcode.com/uploads/2020/02/12/sample_1_1720.png)
> Input: head = [4,2,8], root = [1,4,4,null,2,2,null,1,null,6,8,null,null,null,null,1,3]
> 
> Output: true
---
- ## Solution:
**Code :**
```java
class Solution {
    public boolean isSubPath(ListNode head, TreeNode root) {
        if (head == null) return true;
        if (root == null) return false;
        return (isStartPath(head, root) || isSubPath(head, root.left) || isSubPath(head, root.right));
    }

    private boolean isStartPath(ListNode head, TreeNode root) {
        if (head == null) return true;
        if (root == null) return false;
        return (head.val == root.val) && (isStartPath(head.next, root.left) || isStartPath(head.next, root.right));
    }
}
