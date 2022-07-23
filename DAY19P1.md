# Number of Provinces
---
- ## Question:
> There are n cities. Some of them are connected, while some are not. If city a is connected directly with city b, and city b is connected directly with city c, then city a is connected indirectly with city c.
> 
> A province is a group of directly or indirectly connected cities and no other cities outside of the group.
> 
> You are given an n x n matrix isConnected where isConnected[i][j] = 1 if the ith city and the jth city are directly connected, and isConnected[i][j] = 0 otherwise.
> 
> Return the total number of provinces.
---
- ## Example:
![alt](https://assets.leetcode.com/uploads/2020/12/24/graph1.jpg)
> Input: isConnected = [[1,1,0],[1,1,0],[0,0,1]]
> 
> Output: 2
---
- ## Solution:
**Code :**
```java
class Solution {
    public int findCircleNum(int[][] m) {
        int n=m.length;
        boolean[] visited=new boolean[n+1];
        int count=0;
        for(int i=0;i<n;i++)
        {
            if(!visited[i])
            {
                count++;
                dfs(m,i,visited);
            }
        }
        return count;
    }
    public void dfs(int[][] m,int i,boolean[] visited)
    {
        for(int j=0;j<m[i].length;j++)
        {
            if(!visited[j] && m[i][j]!=0)
            {
                visited[j]=true;
                dfs(m,j,visited);
            }
        }
    }
}
