# Search a 2D Matrix
---
- ## Question:
> Write an efficient algorithm that searches for a value target in an m x n integer matrix matrix. This matrix has the following properties:
>- Integers in each row are sorted from left to right.
>- The first integer of each row is greater than the last integer of the previous row.
---
- ## Example:
![alt](https://assets.leetcode.com/uploads/2020/10/05/mat.jpg)
> Input: matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 3
> 
> Output: true
---
- ## Solution:
**Code :**
```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        int i=0;
        int j=matrix[0].length-1;
        while(i<matrix.length && j>=0)
        {
            if(matrix[i][j]==target)
                return true;
            else if(matrix[i][j]>target)
                j--;
            else 
                i++;
        }
        return false;
    }
}
