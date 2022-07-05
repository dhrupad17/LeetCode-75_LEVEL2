# Spiral Matrix
---
- ## Question:
> Given an m x n matrix, return all elements of the matrix in spiral order.
---
- ## Example:
![alt](https://assets.leetcode.com/uploads/2020/11/13/spiral1.jpg)
> Input: matrix = [[1,2,3],[4,5,6],[7,8,9]]
> 
> Output: [1,2,3,6,9,8,7,4,5]
---
- ## Solution:
**Code :**
```java
class Solution {

    public List<Integer> spiralOrder(int[][] matrix) {
        if(matrix == null || matrix.length == 0 || matrix[0] == null){
            return null;
        }
        int m = matrix[0].length;
        int n = matrix.length;
        List<Integer> ret = new ArrayList<>();
        if(m == 0){
            return ret;
        }
        int left = 0, right = m - 1, up = 0, down = n - 1;
        while(left < right && up < down){
            for(int i = left; i < right; i++){
                ret.add(matrix[up][i]);
            }
            for(int i = up; i < down; i++){
                ret.add(matrix[i][right]);
            }
            for(int i = right; i > left; i--){
                ret.add(matrix[down][i]);
            }
            for(int i = down; i > up; i--){
                ret.add(matrix[i][left]);
            }
            left++;
            right--;
            up++;
            down--;
        }
        // left >= right || up >= down
        if(left > right || up > down){
            return ret;
        }
        if(left == right){
            // still one col left 
            for(int i = up; i <= down; i++){
                ret.add(matrix[i][left]);
            }
        }else{
            for(int i = left; i <= right; i++){
                ret.add(matrix[up][i]);
            }
        }
        return ret;
    }
}
