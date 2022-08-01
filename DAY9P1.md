# Arithmetic Subarrays
--- 
- ## Question:
> A sequence of numbers is called arithmetic if it consists of at least two elements, and the difference between every two consecutive elements is the same. More formally, a sequence s is arithmetic if and only if s[i+1] - s[i] == s[1] - s[0] for all valid i.
> 
> Return a list of boolean elements answer, where answer[i] is true if the subarray nums[l[i]], nums[l[i]+1], ... , nums[r[i]] can be rearranged to form an arithmetic sequence, and false otherwise.
---
- ## Example:
> Input: nums = [4,6,5,9,3,7], l = [0,0,2], r = [2,3,5]
> 
> Output: [true,false,true]
---
- ## Solution:
**Code :**
```java
class Solution {
    public List<Boolean> checkArithmeticSubarrays(int[] nums, int[] l, int[] r) {
        List<Boolean> list = new ArrayList<>();
        for(int i=0;i<l.length;i++){
            int s = l[i];
            int e = r[i];
            int temp[] = Arrays.copyOfRange(nums,s,e+1);
            
            if(check(temp)){
                list.add(true);
            }
            else{
                list.add(false);
            }
        }
        
        return list;
    }
    
    public boolean check(int[]arr){    
        Arrays.sort(arr);
        
        if(arr.length==0||arr.length==1){
            return true;
        }
        else{
            int d = arr[1] - arr[0];
            for(int i=1;i<arr.length;i++){
                if((arr[i]-arr[i-1])!=d){
                    return false;
                }
            }
        }
        return true;
    }
}
