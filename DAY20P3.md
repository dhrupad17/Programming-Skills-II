# My Calendar I
--- 
- ## Question:
> Implement the MyCalendar class:
> 
>- MyCalendar() Initializes the calendar object.
>- boolean book(int start, int end) Returns true if the event can be added to the calendar successfully without causing a double booking. Otherwise, return false and do not add the event to the calendar.
---
- ## Example:
> Input
["MyCalendar", "book", "book", "book"]
[[], [10, 20], [15, 25], [20, 30]]
> 
> Output
[null, true, false, true]
---
- ## Solution:
**Code :**
```java
class MyCalendar {
    
    TreeMap<Integer, Integer> map;
    
    public MyCalendar() {
        map = new TreeMap();
    }
    
    public boolean book(int start, int end) {
        Integer smallerKey = map.floorKey(start), greaterKey = map.ceilingKey(start);
        
        if (smallerKey == null || map.get(smallerKey) <= start) {
            if (greaterKey == null || greaterKey >= end) {
                map.put(start, end);
                return true;
            }
        } 
        return false;
    }
}
