# Design Circular Queue
--- 
- ## Question:
> Implementation the MyCircularQueue class:
> 
>- MyCircularQueue(k) Initializes the object with the size of the queue to be k.
>- int Front() Gets the front item from the queue. If the queue is empty, return -1.
>- int Rear() Gets the last item from the queue. If the queue is empty, return -1.
>- boolean enQueue(int value) Inserts an element into the circular queue. Return true if the operation is successful.
>- boolean deQueue() Deletes an element from the circular queue. Return true if the operation is successful.
>- boolean isEmpty() Checks whether the circular queue is empty or not.
>- boolean isFull() Checks whether the circular queue is full or not.
---
- ## Example:
> Input
["MyCircularQueue", "enQueue", "enQueue", "enQueue", "enQueue", "Rear", "isFull", "deQueue", "enQueue", "Rear"]
[[3], [1], [2], [3], [4], [], [], [], [4], []]
> 
> Output
[null, true, true, true, false, 3, true, true, true, 4]
---
- ## Solution:
**Code :**
```java
class MyCircularQueue {
    public int[] arr;
    public int head;
    public int tail;
    public int length;
    public MyCircularQueue(int k) {
        this.arr = new int[k];
        this.head=this.tail=-1;
        this.length=k;
    }
    
    public boolean enQueue(int value) {
        if(this.head==-1){
            this.head++;
            this.tail++;
            this.arr[this.head]=value;
            return true;
        }
        if(((this.tail+1)%this.length) != this.head){
            this.tail=(this.tail+1)%this.length;
            this.arr[this.tail]=value;
            return true;
        }
        return false;            
    }
    
    public boolean deQueue() {
        if(this.head==-1) return false;
        if(this.head==this.tail){
            this.head=this.tail=-1;
            return true;
        }
        this.head=(this.head+1)%this.length;
        return true;
    }
    
    public int Front() {
        if(this.head==-1) return -1;
        return this.arr[this.head];
    }
    
    public int Rear() {
        if(this.head==-1) return -1;
        return this.arr[this.tail];
    }
    
    public boolean isEmpty() {
        return this.head==-1;
    }
    
    public boolean isFull() {
        return this.head==(this.tail+1)%this.length;
    }
}
