# Partition Equal Subset Sum
---
- ## Question:
> Given a non-empty array nums containing only positive integers, find if the array can be partitioned into two subsets such that the sum of elements in both subsets is equal.
---
- ## Example:
> Input: nums = [1,5,11,5]
> 
> Output: true
> 
> Explanation: The array can be partitioned as [1, 5, 5] and [11].
---
- ## Solution:
**Code :**
```java
class Solution {
    public boolean canPartition(int[] nums) {
        int sum=0;
        int n=nums.length;
        for(int i: nums)
            sum=sum+i;
        if(sum%2!=0)
            return false;
        sum=sum/2;
        boolean dp[][]=new boolean[n+1][sum+1];
        for(int i=0;i<=n;i++)
        {
            for(int j=0;j<=sum;j++)
            {
                if(i==0||j==0)
                    dp[i][j]=false;
                else if(nums[i-1]>j)
                    dp[i][j]=dp[i-1][j];
                else if(nums[i-1]==j)
                    dp[i][j]=true;
                else
                    dp[i][j]=dp[i-1][j]||dp[i-1][j-nums[i-1]];
            }
        }
        return dp[n][sum];
    }
}
