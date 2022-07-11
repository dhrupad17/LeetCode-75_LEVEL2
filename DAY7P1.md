# Diameter of Binary Tree
---
- ## Question:
> Given the root of a binary tree, return the length of the diameter of the tree.
> 
> The diameter of a binary tree is the length of the longest path between any two nodes in a tree. This path may or may not pass through the root.
> 
> The length of a path between two nodes is represented by the number of edges between them.
---
- ## Example:
![alt](https://assets.leetcode.com/uploads/2021/03/06/diamtree.jpg)
> Input: root = [1,2,3,4,5]
> 
> Output: 3
> 
> Explanation: 3 is the length of the path [4,2,1,3] or [5,2,1,3].
---
- ## Solution:
**Code :**
```java
class Solution {
    int ans=0;
    public int diameterOfBinaryTree(TreeNode root) {
        if(root==null )return 0;
        height(root);
        return ans;
    }
    
    public int height(TreeNode root){
        //if root==null height==0
        if(root==null)return -1;
        
        int L=height(root.left);
        int R=height(root.right);
        //ans signfies(no. of nodes farthest apart) or the DIAMETER
        ans=Math.max(ans,L+R+2);
        //height of the tree is max of LST & RST +1
        return 1+Math.max(L,R);
    }
}
