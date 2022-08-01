# N-ary Tree Level Order Traversal
--- 
- ## Question:
> Given an n-ary tree, return the level order traversal of its nodes' values.
> 
> Nary-Tree input serialization is represented in their level order traversal, each group of children is separated by the null value (See examples).
---
- ## Example:
![ALT](https://assets.leetcode.com/uploads/2018/10/12/narytreeexample.png)
> Input: root = [1,null,3,2,4,null,5,6]
> 
> Output: [[1],[3,2,4],[5,6]]
---
- ## Solution:
**Code :**
```java
class Solution {
    List<List<Integer>> ans=new ArrayList<List<Integer>>();
    public List<List<Integer>> levelOrder(Node root) {
        solve(root,0);
        return ans;
    }
    public void solve(Node root,int h)
    {
        if(root==null)
            return;
        if(ans.size()==h)
        {
            ans.add(new ArrayList<Integer>());
        }
        ans.get(h).add(root.val);
        for(Node child:root.children)
        {
            solve(child,h+1);
        }
    }
}
