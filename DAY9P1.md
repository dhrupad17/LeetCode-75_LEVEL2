# Convert Sorted Array to Binary Search Tree
---
- ## Question:
> Given an integer array nums where the elements are sorted in ascending order, convert it to a height-balanced binary search tree.
> 
> A height-balanced binary tree is a binary tree in which the depth of the two subtrees of every node never differs by more than one.
---
- ## Example:
![alt](https://assets.leetcode.com/uploads/2021/02/18/btree1.jpg)
> Input: nums = [-10,-3,0,5,9]
> 
> Output: [0,-3,9,-10,null,5]
> 
> Explanation: [0,-10,5,null,-3,null,9] is also accepted:
> 
![alt](https://assets.leetcode.com/uploads/2021/02/18/btree2.jpg)
---
- ## Solution:
**Code :**
```java
class Solution {
    public TreeNode sortedArrayToBST(int[] nums) {
        return help(nums,0,nums.length-1);
    }
    private TreeNode help(int[] nums, int l, int r)
    {
        if(l>r)
            return null;
        int mid=l+(r-l)/2;
        TreeNode root=new TreeNode(nums[mid]);
        root.left=help(nums,l,mid-1);
        root.right=help(nums,mid+1,r);
        return root;
    }
}
