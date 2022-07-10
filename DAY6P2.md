# Balanced Binary Tree
---
- ## Question:
> Given a binary tree, determine if it is height-balanced.
> 
> For this problem, a height-balanced binary tree is defined as:
>- a binary tree in which the left and right subtrees of every node differ in height by no more than 1.
---
- ## Example:
![alt](https://assets.leetcode.com/uploads/2020/10/06/balance_1.jpg)
> Input: root = [3,9,20,null,null,15,7]
> 
> Output: true
---
- ## Solution:
**Code :**
```java
class Solution {
    public boolean isBalanced(TreeNode root) {
    if(root==null) return true;
    int l=depth(root.left);
    int r=depth(root.right);
    return ((int)Math.abs(l-r)<2)&&isBalanced(root.left) && isBalanced(root.right);
}
static int depth(TreeNode n){
        if(n==null) return 0;
        return Math.max(depth(n.left),depth(n.right))+1;
   }
}
