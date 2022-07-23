# Monotonic Array
--- 
- ## Question:
> An array is monotonic if it is either monotone increasing or monotone decreasing.
> 
> An array nums is monotone increasing if for all i <= j, nums[i] <= nums[j]. An array nums is monotone decreasing if for all i <= j, nums[i] >= nums[j].
> 
> Given an integer array nums, return true if the given array is monotonic, or false otherwise.
---
- ## Example:
> Input: nums = [1,2,2,3]
> 
> Output: true
---
- ## Solution:
**Code :**
```java
class Solution {
    public boolean isMonotonic(int[] nums) {
        if(nums.length==1)
            return true;
        int n=nums.length;
        boolean help=(nums[n-1]-nums[0])>0;
        for(int i=0;i<n-1;i++)
        {
            if(nums[i]!=nums[i+1]&& (nums[i+1]-nums[i]>0!=help))
                return false;
        }
        return true;
    }
}
