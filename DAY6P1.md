# Daily Temperatures
--- 
- ## Question:
> Given an array of integers temperatures represents the daily temperatures, return an array answer such that answer[i] is the number of days you have to wait after the ith day to get a warmer temperature. If there is no future day for which this is possible, keep answer[i] == 0 instead.
---
- ## Example:
> Input: temperatures = [73,74,75,71,69,72,76,73]
> 
> Output: [1,1,4,2,1,1,0,0]
---
- ## Solution:
**Code :**
```java
class Solution {
    public int[] dailyTemperatures(int[] t){
    Stack<Integer> st= new Stack();
    int n=t.length;
    int ans[]=new int[n];
    for(int i=0;i<n;i++)
    {
        while(st.size()>0 && t[i]>t[st.peek()])
            ans[st.peek()]=i-st.pop();
        
        st.push(i);
    }
    return ans;
	}
}
