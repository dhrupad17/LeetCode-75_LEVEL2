# Path Sum III
---
- ## Question:
> Given the root of a binary tree and an integer targetSum, return the number of paths where the sum of the values along the path equals targetSum.
> 
> The path does not need to start or end at the root or a leaf, but it must go downwards (i.e., traveling only from parent nodes to child nodes).
---
- ## Example:
![alt](https://assets.leetcode.com/uploads/2021/04/09/pathsum3-1-tree.jpg)
> Input: root = [10,5,-3,3,2,null,11,3,-2,null,1], targetSum = 8
> 
> Output: 3
> 
> Explanation: The paths that sum to 8 are shown.
---
- ## Solution:
**Code :**
```java
class Solution {
    public int pathSum(TreeNode root, int targetSum) {
        int[] count=new int[1];
        ArrayList<Integer> ans=new ArrayList<Integer>();
        if(root==null)
            return 0;
        helper(root,targetSum,count,ans);
        return count[0];
    }
    public void helper(TreeNode root,int targetSum,int[] count,ArrayList<Integer> ans)
    {
        if(root==null)
            return;
        ans.add(root.val);
        int sum=0;
        for(int i=ans.size()-1;i>=0;i--)
        {
            sum=sum+ans.get(i);
            if(sum==targetSum)
            {
                count[0]++;
            }
        }
        helper(root.left,targetSum,count,ans);
        helper(root.right,targetSum,count,ans);
        ans.remove(ans.size()-1);
    }
}
