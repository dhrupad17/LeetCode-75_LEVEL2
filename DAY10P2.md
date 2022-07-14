# Pacific Atlantic Water Flow
---
- ## Question:
> There is an m x n rectangular island that borders both the Pacific Ocean and Atlantic Ocean. The Pacific Ocean touches the island's left and top edges, and the Atlantic Ocean touches the island's right and bottom edges.
> 
> The island is partitioned into a grid of square cells. You are given an m x n integer matrix heights where heights[r][c] represents the height above sea level of the cell at coordinate (r, c).
> 
> The island receives a lot of rain, and the rain water can flow to neighboring cells directly north, south, east, and west if the neighboring cell's height is less than or equal to the current cell's height. Water can flow from any cell adjacent to an ocean into the ocean.
> 
> Return a 2D list of grid coordinates result where result[i] = [ri, ci] denotes that rain water can flow from cell (ri, ci) to both the Pacific and Atlantic oceans.
---
- ## Example:
![alt](https://assets.leetcode.com/uploads/2021/06/08/waterflow-grid.jpg)
> Input: heights = [[1,2,2,3,5],[3,2,3,4,4],[2,4,5,3,1],[6,7,1,4,5],[5,1,1,2,4]]
> 
> Output: [[0,4],[1,3],[1,4],[2,2],[3,0],[3,1],[4,0]]
---
- ## Solution:
**Code :**
```java
class Solution {
    static int[][] dir={{0,1},{0,-1},{1,0},{-1,0}};
    public List<List<Integer>> pacificAtlantic(int[][] heights) {
        List<List<Integer>> ans=new ArrayList<>();
        int m=heights.length;
        int n=heights[0].length;
        boolean[][] pac=new boolean[heights.length][heights[0].length];
        boolean[][] atl=new boolean[heights.length][heights[0].length];
        
        for(int i=0;i<n;i++){
            dfs(heights,0,i,Integer.MIN_VALUE,pac);
            dfs(heights,m-1,i,Integer.MIN_VALUE,atl);
        }
        for(int j=0;j<m;j++){
            dfs(heights,j,0,Integer.MIN_VALUE,pac);
            dfs(heights,j,n-1,Integer.MIN_VALUE,atl);
        }
        for(int i=0;i<m;i++){
            for(int j=0;j<n;j++){
               if(pac[i][j] && atl[i][j]){
                   List<Integer> l=new ArrayList<>();
                   l.add(i);
                   l.add(j);
                   ans.add(l);
               }
            }
        }
        return ans;
    }
    public static void dfs(int[][] heights,int i, int j,int prev, boolean[][] arr){
        if(i<0 || j<0 || i>=heights.length || j>=heights[0].length || arr[i][j]==true || heights[i][j]<prev)return;
        
        arr[i][j]=true;
        for(int k=0;k<4;k++){
            int x=i+dir[k][0];
            int y=j+dir[k][1];
            
            dfs(heights,x,y,heights[i][j],arr);
        }
        
        
    }
}
