# 3Sum Closest
---
- ## Question:
> Given an integer array nums of length n and an integer target, find three integers in nums such that the sum is closest to target.
> 
> Return the sum of the three integers.
> 
> You may assume that each input would have exactly one solution.
---
- ## Example:
> Input: nums = [-1,2,1,-4], target = 1
> 
> Output: 2
> 
> Explanation: The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).
---
- ## Solution:
**Code :**
```java
class Solution {
    public int threeSumClosest(int[] nums, int target) {
        int diff=Integer.MAX_VALUE;
        int sum=0;
        Arrays.sort(nums);
        for(int i=0;i<nums.length;i++)
        {
            int left=i+1;
            int right=nums.length-1;
        while(left<right)
        {
            sum=nums[i]+nums[left]+nums[right];
            if(Math.abs(target-sum)<Math.abs(diff))
            {
                diff=target-sum;
            }
            if(sum>target)
            {
                right--;
            }
            else
                left++;
        }
        }
        return target-diff;
    }
}
