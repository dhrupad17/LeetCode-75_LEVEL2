# Maximum Product Subarray
---
- ## Question:
> Given an integer array nums, find a contiguous non-empty subarray within the array that has the largest product, and return the product.
> 
> The test cases are generated so that the answer will fit in a 32-bit integer.
> 
> A subarray is a contiguous subsequence of the array.
---
- ## Example:
> Input: nums = [2,3,-2,4]
> 
> Output: 6
> 
> Explanation: [2,3] has the largest product 6.
---
- ## Solution:
**Code :**
```java
class Solution {
    public int maxProduct(int[] nums) {
        int max=nums[0],min=nums[0],ans=nums[0];
        for(int i=1;i<nums.length;i++)
        {
            int temp=max;
            max=Math.max(Math.max(max*nums[i],min*nums[i]),nums[i]);
            min=Math.min(Math.min(temp*nums[i],min*nums[i]),nums[i]);
            
            if(max>ans)
            {
                ans=max;
            }
        }
        return ans;
    }
}
