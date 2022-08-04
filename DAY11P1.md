# Time Needed to Inform All Employees
--- 
- ## Question:
> A company has n employees with a unique ID for each employee from 0 to n - 1. The head of the company is the one with headID.
> 
> Each employee has one direct manager given in the manager array where manager[i] is the direct manager of the i-th employee, manager[headID] = -1. Also, it is guaranteed that the subordination relationships have a tree structure.
> 
> The head of the company wants to inform all the company employees of an urgent piece of news. He will inform his direct subordinates, and they will inform their subordinates, and so on until all employees know about the urgent news.
> 
> The i-th employee needs informTime[i] minutes to inform all of his direct subordinates (i.e., After informTime[i] minutes, all his direct subordinates can start spreading the news).
> 
> Return the number of minutes needed to inform all the employees about the urgent news.
---
- ## Example:
> Input: n = 1, headID = 0, manager = [-1], informTime = [0]
> 
> Output: 0
> 
> Explanation: The head of the company is the only employee in the company.
---
- ## Solution:
**Code :**
```java
class Solution {
    int ans;
    public int numOfMinutes(int n, int headID, int[] manager, int[] informTime) {
        ans = Integer.MIN_VALUE;
        Map<Integer,List<Integer>> map = new HashMap<>();
        
        int len = manager.length;
        
        for(int i = 0; i < len; ++i){
            int boss = manager[i];
            if(boss!=-1){
                if(map.get(boss) == null){
                    map.put(boss, new LinkedList<Integer>());
                }
                map.get(boss).add(i);
            }
        }
        
        // call dfs
        dfs(map,informTime, headID,manager,0);
        return ans;
    }
    
    
    // dfs: get every one's worker and add time, when reach the leaf, compare the max with ans
    public void dfs(Map<Integer,List<Integer>> map, int[] time, int root, int[] manager,int max){
        
        // base case: reach leaf, no more woker
        if( map.get(root) == null){
            ans = Math.max(max,ans);
            return;
        }
        
        // recursion: find all woker and call dfs
        List<Integer> li = map.get(root);
        max += time[root];
        
        for(int worker : li){
            dfs(map,time,worker,manager,max);    
        }
        
    }
}
