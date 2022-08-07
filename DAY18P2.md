# Flatten Nested List Iterator
--- 
- ## Question:
> You are given a nested list of integers nestedList. Each element is either an integer or a list whose elements may also be integers or other lists. Implement an iterator to flatten it.
---
- ## Example:
> Input: nestedList = [[1,1],2,[1,1]]
> 
> Output: [1,1,2,1,1]
---
- ## Solution:
**Code :**
```c++
class NestedIterator {
    vector<int> v;
    int pos=0;
public:
    NestedIterator(vector<NestedInteger> &nestedList) {
        flatten(nestedList);
    }
    
    void flatten(vector<NestedInteger> &nestedList)
    {
        for(auto x : nestedList)
        {
            if(x.isInteger())
                v.push_back(x.getInteger());
            else
                flatten(x.getList());
        }
    }
    
    int next() {
        return v[pos++];
    }
    
    bool hasNext() {
        return pos < v.size();
    }
};
