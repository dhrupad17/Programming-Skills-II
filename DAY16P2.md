# Binary Search Tree Iterator
--- 
- ## Question:
> Implement the BSTIterator class that represents an iterator over the in-order traversal of a binary search tree (BST)
---
- ## Example:
![ALT](https://assets.leetcode.com/uploads/2018/12/25/bst-tree.png)
> Input
["BSTIterator", "next", "next", "hasNext", "next", "hasNext", "next", "hasNext", "next", "hasNext"]
[[[7, 3, 15, null, null, 9, 20]], [], [], [], [], [], [], [], [], []]
> 
> Output
[null, 3, 7, true, 9, true, 15, true, 20, false]
---
- ## Solution:
**Code :**
```java
public class BSTIterator {
    private Stack<TreeNode> stack = new Stack<TreeNode>();
    
    public BSTIterator(TreeNode root) {
        pushAll(root);
    }

    /** @return whether we have a next smallest number */
    public boolean hasNext() {
        return !stack.isEmpty();
    }

    /** @return the next smallest number */
    public int next() {
        TreeNode tmpNode = stack.pop();
        pushAll(tmpNode.right);
        return tmpNode.val;
    }
    
    private void pushAll(TreeNode node) {
        for (; node != null; stack.push(node), node = node.left);
    }
}
