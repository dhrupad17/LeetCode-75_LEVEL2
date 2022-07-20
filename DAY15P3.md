# Binary Tree Right Side View
---
- ## Question:
> Given the root of a binary tree, imagine yourself standing on the right side of it, return the values of the nodes you can see ordered from top to bottom.
---
- ## Example:
![alt](https://assets.leetcode.com/uploads/2021/02/14/tree.jpg)
> Input: root = [1,2,3,null,5,null,4]
> 
> Output: [1,3,4]
---
- ## Solution:
**Code :**
```java
public class Solution {
    public List<Integer> rightSideView(TreeNode root) {
        Queue<TreeNode> queue = new LinkedList<>();
        List<Integer> rst = new ArrayList<>();
        if(root == null) return rst;
        
        queue.offer(root);
        while(!queue.isEmpty()){
            int levelNum = queue.size();
            for(int i = 0; i < levelNum; i++){
                if(queue.peek().left != null) queue.offer(queue.peek().left);
                if(queue.peek().right != null) queue.offer(queue.peek().right);
                if(i == levelNum - 1) rst.add(queue.poll().val);
                else queue.poll();
            }
        }
        return rst;
    }
}
