# Symmetric Tree
---
- ## Question:
> Given the root of a binary tree, check whether it is a mirror of itself (i.e., symmetric around its center).
---
- ## Example:
![alt](https://assets.leetcode.com/uploads/2021/02/19/symtree1.jpg)
> Input: root = [1,2,2,3,4,4,3]
> 
> Output: true
---
- ## Solution:
**Code :**
```java
class Solution {
    public boolean isSymmetric(TreeNode root) {
        return root==null|| help(root.left,root.right);
    }
    public boolean help(TreeNode left,TreeNode right)
    {
        if(left==null|| right==null)
            return left==right;
        if(left.val!=right.val)
            return false;
        return help(left.left,right.right)&& help(left.right,right.left);
    }
}
