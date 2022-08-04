# Next Greater Element II
--- 
- ## Question:
> Given a circular integer array nums (i.e., the next element of nums[nums.length - 1] is nums[0]), return the next greater number for every element in nums.
> 
> The next greater number of a number x is the first greater number to its traversing-order next in the array, which means you could search circularly to find its next greater number. If it doesn't exist, return -1 for this number.
---
- ## Example:
> Input: nums = [1,2,1]
> 
> Output: [2,-1,2]
---
- ## Solution:
**Code :**
```java
class Solution {
    public int[] nextGreaterElements(int[] nums) {
        int len=2*nums.length-1;
        int[] result=new int[nums.length];
        Arrays.fill(result,-1);
        Stack<Integer> st=new Stack<>();
        for(int i=0;i<len;i++)
        {
            int index=i%nums.length;
            while(!st.isEmpty()&& nums[st.peek()]<nums[index])
            {
                int pop=st.pop();
                result[pop]=nums[index];
            }
            st.push(index);
        }
        return result;
    }
}
