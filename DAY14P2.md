# Copy List with Random Pointer
--- 
- ## Question:
> A linked list of length n is given such that each node contains an additional random pointer, which could point to any node in the list, or null.
> 
> Construct a deep copy of the list. The deep copy should consist of exactly n brand new nodes, where each new node has its value set to the value of its corresponding original node. Both the next and random pointer of the new nodes should point to new nodes in the copied list such that the pointers in the original list and copied list represent the same list state. None of the pointers in the new list should point to nodes in the original list.
> 
> For example, if there are two nodes X and Y in the original list, where X.random --> Y, then for the corresponding two nodes x and y in the copied list, x.random --> y.
> 
> Return the head of the copied linked list.
---
- ## Example:
> Input: head = [[7,null],[13,0],[11,4],[10,2],[1,0]]
> 
> Output: [[7,null],[13,0],[11,4],[10,2],[1,0]]
---
- ## Solution:
**Code :**
```java
class Solution {
    public Node copyRandomList(Node head) {
        Node main_head = head;
        if(head == null)
            return null;
        
        Node tmp_head = new Node(head.val);
        
        Node cur_main = head;
        Node cur_tmp = tmp_head;
        
        while(cur_main != null) {
            if(cur_tmp == null)
                cur_tmp = new Node(cur_main.val);
            
            Node cur_next_main = cur_main.next;
            cur_main.next = cur_tmp;
            cur_tmp.next = cur_next_main;
            cur_tmp.random = cur_main.random;
            cur_main = cur_next_main;
            cur_tmp = null;
        }
        
        cur_main = head;
        cur_tmp = tmp_head;
        
        while(cur_tmp != null) {
            Node cur_tmp_next = cur_tmp.next != null ? cur_tmp.next.next:null;
            cur_tmp.random = cur_tmp.random != null?cur_tmp.random.next : null;
            cur_tmp = cur_tmp_next;
        }
        cur_tmp = tmp_head;
        while(cur_tmp != null) {
            Node cur_tmp_next = cur_tmp.next != null ? cur_tmp.next.next:null;
            cur_main.next = cur_tmp.next;
            cur_tmp.next = cur_tmp_next;
            cur_main = cur_main.next;
            cur_tmp = cur_tmp.next;
        }
        
        return tmp_head;
    }
}
