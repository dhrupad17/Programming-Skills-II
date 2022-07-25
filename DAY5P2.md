# Add to Array-Form of Integer
--- 
- ## Question:
> Given num, the array-form of an integer, and an integer k, return the array-form of the integer num + k.
---
- ## Example:
> Input: num = [1,2,0,0], k = 34
> 
> Output: [1,2,3,4]
> 
> Explanation: 1200 + 34 = 1234
---
- ## Solution:
**Code :**
```java
class Solution {
    public List<Integer> addToArrayForm(int[] num, int k) {
        List<Integer> L=new ArrayList<>();
        // int ans=0;
        for(int i=num.length-1;i>=0;i--)
        {
            int ans=num[i]+k;
            L.add(ans%10);
            k=ans/10;
        }
        while(k>0)
        {
            int d=k%10;
            k=k/10;
            L.add(d);
        }
        Collections.reverse(L);
        return L;
    }
}
