# Subarray Product Less Than K
--- 
- ## Question:
> Given an array of integers nums and an integer k, return the number of contiguous subarrays where the product of all the elements in the subarray is strictly less than k.
---
- ## Example:
> Input: nums = [10,5,2,6], k = 100
> 
> Output: 8
> 
> Explanation: The 8 subarrays that have product less than 100 are:
> 
> [10], [5], [2], [6], [10, 5], [5, 2], [2, 6], [5, 2, 6]
> 
> Note that [10, 5, 2] is not included as the product of 100 is not strictly less than k. 
---
- ## Solution:
**Code :**
```java
class Solution {
    public int numSubarrayProductLessThanK(int[] nums, int k) {
        int count=0;
        int prod=1;
        int winstart=0;
        if(k<=1)
            return 0;
        for(int winend=0;winend<nums.length;winend++)
        {
            prod=prod*nums[winend];
            while(prod>=k)
            {
                prod=prod/nums[winstart];
                winstart++;
            }
            count=count+winend-winstart+1;
        }
        return count;
    }
}
