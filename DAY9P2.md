# Kth Smallest Element in a BST
---
- ## Question:
> Given the root of a binary search tree, and an integer k, return the kth smallest value (1-indexed) of all the values of the nodes in the tree.
---
- ## Example:
> Input: root = [3,1,4,null,2], k = 1
> 
> Output: 1
---
- ## Solution:
**Code :**
```java
class Solution {
    int ans,count;
    public int kthSmallest(TreeNode root, int k) {
        ans=-1;
        count=0;
        solve(root,k);
        return ans;
    }
    public void solve(TreeNode root,int k)
    {
        if(root==null)
            return;
        solve(root.left,k);
        count++;
        if(count==k)
        {
            ans=root.val;
        }
        solve(root.right,k);
    }
}
