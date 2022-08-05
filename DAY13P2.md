# Smallest Range II
--- 
- ## Question:
> You are given an integer array nums and an integer k.
> 
> For each index i where 0 <= i < nums.length, change nums[i] to be either nums[i] + k or nums[i] - k.
> 
> The score of nums is the difference between the maximum and minimum elements in nums.
> 
> Return the minimum score of nums after changing the values at each index.
---
- ## Example:
> Input: nums = [1], k = 0
> 
> Output: 0
> 
> Explanation: The score is max(nums) - min(nums) = 1 - 1 = 0.
---
- ## Solution:
**Code :**
```java
class Solution {
    public int smallestRangeII(int[] nums, int k) {
        Arrays.sort(nums);
        int p=nums.length;
        int res=nums[p-1]-nums[0];
        if(p==1)
            return 0;
        for(int i=0;i<p-1;i++)
        {
            int a=Math.min(nums[0]+k,nums[i+1]-k);
            int b=Math.max(nums[p-1]-k,nums[i]+k);
            res=Math.min(res,b-a);
        }
        return res;
    }
    
}
