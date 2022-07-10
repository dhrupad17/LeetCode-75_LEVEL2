# Invert Binary Tree
---
- ## Question:
> Given the root of a binary tree, invert the tree, and return its root.
---
- ## Example:
![alt](https://assets.leetcode.com/uploads/2021/03/14/invert1-tree.jpg)
> Input: root = [4,2,7,1,3,6,9]
> 
> Output: [4,7,2,9,6,3,1]
---
- ## Solution:
**Code :**
```java
class Solution {
    public TreeNode invertTree(TreeNode root) {
        if(root==null)
            return null;
        TreeNode left=invertTree(root.left);
        TreeNode right=invertTree(root.right);
        root.left=right;
        root.right=left;
        return root;
    }
}
