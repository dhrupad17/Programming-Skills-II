# Design Linked List
--- 
- ## Question:
> Design your implementation of the linked list. You can choose to use a singly or doubly linked list.
A node in a singly linked list should have two attributes: val and next. val is the value of the current node, and next is a pointer/reference to the next node.
If you want to use the doubly linked list, you will need one more attribute prev to indicate the previous node in the linked list. Assume all nodes in the linked list are 0-indexed.
---
- ## Example:
> Input
["MyLinkedList", "addAtHead", "addAtTail", "addAtIndex", "get", "deleteAtIndex", "get"]
[[], [1], [3], [1, 2], [1], [1], [1]]
>
> Output
[null, null, null, null, 2, null, 3]
---
- ## Solution:
**Code :**
```java
class MyLinkedList {
    // Linked List Node
    class ListNode {
        int val;
        ListNode next;
        ListNode(int val) {
            this.val = val;
            this.next = null;
        }
    }

    // keep track of head, tail and length of Linked List
    private ListNode head;
    private ListNode tail;
    private int length;

    public MyLinkedList() {
        // initialize
        this.head = null;
        this.tail = null;
        this.length = 0;
    }

    // helper function to get the node at a given index
    private ListNode getNode(int index) {
        // check if index is valid
        if(index < 0 || index >= this.length)
            return null;
        ListNode node = this.head;
        for(int i = 0; i < index && node != null; i++)
            node = node.next;
        return node;
    }
    
    public int get(int index) {
        ListNode node = getNode(index);
        return (node == null) ? -1 : node.val;
    }
    
    public void addAtHead(int val) {
        ListNode newNode = new ListNode(val);
        newNode.next = this.head;
        // update tail if Linked List is empty
        if(this.head == null)
            this.tail = newNode;
        // update head
        this.head = newNode;
        this.length += 1;
    }
    
    public void addAtTail(int val) {
        if(this.head == null) {
            addAtHead(val);
            return;
        }
        ListNode newNode = new ListNode(val);
        this.tail.next = newNode;
        // update tail
        this.tail = newNode;
        this.length += 1;
    }
    
    public void addAtIndex(int index, int val) {
        // check if index is valid
        if(index < 0 || index > this.length)
            return;
        // add at beginning of Linked List
        if(index == 0) {
            addAtHead(val);
            return;
        }
        // add at end of Linked List
        if(index == this.length) {
            addAtTail(val);
            return;
        }
        ListNode node = getNode(index - 1);
        if(node == null)
            return;
        ListNode newNode = new ListNode(val);
        newNode.next = node.next;
        node.next = newNode;
        this.length += 1;
    }
    
    public void deleteAtIndex(int index) {
        // check if index is valid
        if(index < 0 || index >= this.length)
            return;
        // delete at beginning of Linked List
        if(index == 0) {
            this.head = this.head.next;
            this.length -= 1;
            return;
        }
        ListNode node = getNode(index - 1);
        if(node == null || node.next == null)
            return;
        node.next = node.next.next;
        // update tail if deleting at end of Linked List
        if(node.next == null)
            this.tail = node;
        this.length -= 1;
    }
}
