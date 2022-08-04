# Next Greater Element III
--- 
- ## Question:
> Given a positive integer n, find the smallest integer which has exactly the same digits existing in the integer n and is greater in value than n. If no such positive integer exists, return -1.
> 
> Note that the returned integer should fit in 32-bit integer, if there is a valid answer but it does not fit in 32-bit integer, return -1.
---
- ## Example:
> Input: n = 12
> 
> Output: 21
---
- ## Solution:
**Code :**
```java
class Solution {
    public int nextGreaterElement(int n) {
        if(n<=11) return -1;
        char[] nums = String.valueOf(n).toCharArray();
        
        int idx = -1;
        for(int i=nums.length-2;i>=0;i--){
            if(nums[i]<nums[i+1]){
                idx = i;
                break;
            }
        }
        if(idx==-1) return -1;
        
        int y = binarySearch(nums,idx+1,nums.length-1,nums[idx]);
        swap(nums,idx,y);
        for(int i=idx+1,j = nums.length-1;i<j;i++,j--){
            swap(nums,i,j);
        }
        try{
            return Integer.parseInt(String.valueOf(nums));
        }
        catch(Exception e){
            return -1;
        }
    }
    private int binarySearch(char[] nums,int i,int j,char target){
        while(i<=j){
            int mid = j+(i-j)/2;
            if(nums[mid]<=target) 
                j = mid-1;
            else i = mid + 1;
        }
        return j;
    }
    private void swap(char[] nums,int i,int j){
        char t = nums[i];
        nums[i] = nums[j];
        nums[j] = t;
    }
}
