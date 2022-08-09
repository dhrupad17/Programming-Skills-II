# Insert Delete GetRandom O(1)
--- 
- ## Question:
> Implement the RandomizedSet class:
> 
>- RandomizedSet() Initializes the RandomizedSet object.
>- bool insert(int val) Inserts an item val into the set if not present. Returns true if the item was not present, false otherwise.
>- bool remove(int val) Removes an item val from the set if present. Returns true if the item was present, false otherwise.
>- int getRandom() Returns a random element from the current set of elements (it's guaranteed that at least one element exists when this method is called). Each element must have the same probability of being returned.
---
- ## Example:
> Input
["RandomizedSet", "insert", "remove", "insert", "getRandom", "remove", "insert", "getRandom"]
[[], [1], [2], [2], [], [1], [2], []]
> 
> Output
[null, true, false, true, 2, true, false, 2]
---
- ## Solution:
**Code :**
```java
class RandomizedSet {
    
    List<Integer> vals;
    Map<Integer,Integer> pos_of;

    public RandomizedSet() {
        vals = new ArrayList<Integer>();
        pos_of = new HashMap<Integer, Integer>();
    }
    
    public void swap(int i, int j) {
        int tmp = vals.get(i);
        vals.set(i, vals.get(j));
        vals.set(j, tmp); 
    }
    
    public boolean insert(int val) {
        if (pos_of.containsKey(val)) return false;
        vals.add(val);
        pos_of.put(val, vals.size()-1);
        return true; 
    }
    
    public boolean remove(int val) {
        if (!pos_of.containsKey(val)) return false;
        int pr = vals.get(vals.size()-1);
        swap(pos_of.get(val), vals.size()-1);
        pos_of.put(pr, pos_of.get(val));
        pos_of.remove(val);
        vals.remove(vals.size()-1); 
        return true;
    }
    
    public int getRandom() {
        return vals.get((new Random()).nextInt(vals.size()) % vals.size());
    }
}
