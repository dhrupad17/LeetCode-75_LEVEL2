# Course Schedule II
---
- ## Question:
> There are a total of numCourses courses you have to take, labeled from 0 to numCourses - 1. You are given an array prerequisites where prerequisites[i] = [ai, bi] indicates that you must take course bi first if you want to take course ai.
> 
> For example, the pair [0, 1], indicates that to take course 0 you have to first take course 1.
> 
> Return the ordering of courses you should take to finish all courses. If there are many valid answers, return any of them. If it is impossible to finish all courses, return an empty array.
---
- ## Example:
> Input: numCourses = 2, prerequisites = [[1,0]]
> 
> Output: [0,1]
> 
> Explanation: There are a total of 2 courses to take. To take course 1 you should have finished course 0. So the correct course order is [0,1].
---
- ## Solution:
**Code :**
```java
class Solution {
    public int[] findOrder(int numCourses, int[][] prerequisites) {
        List<List<Integer>> graph = new ArrayList<>();
        for(int i=0;i<numCourses;i++)
            graph.add(new ArrayList<>());
        
        for(int[] pre:prerequisites)
            graph.get(pre[1]).add(pre[0]);
        
        boolean[] checked = new boolean[numCourses];
        Stack<Integer> stack = new Stack<>();
        for(int i=0;i<numCourses;i++){
            boolean[] path = new boolean[numCourses];
            if(isCyclic(i,graph,stack,path,checked)==true)
                return new int[0];
        }
        int[] res = new int[numCourses];
        for(int i=0;i<numCourses;i++)
            res[i] = stack.pop();
        return res;
    }
    
    boolean isCyclic(int node,List<List<Integer>> graph,Stack<Integer> stack,boolean[] path,boolean[] checked){
        if(checked[node]==true)
            return false;
        if(path[node]==true)
            return true;
        path[node] = true;
        for(int adj:graph.get(node)){
            if(isCyclic(adj,graph,stack,path,checked)==true)
                return true;
        }
        stack.push(node);
        path[node] = false;
        checked[node] = true;
        return false;
    }
}
