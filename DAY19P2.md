# Most Stones Removed with Same Row or Column
---
- ## Question:
> On a 2D plane, we place n stones at some integer coordinate points. Each coordinate point may have at most one stone.
> 
> A stone can be removed if it shares either the same row or the same column as another stone that has not been removed.
> 
> Given an array stones of length n where stones[i] = [xi, yi] represents the location of the ith stone, return the largest possible number of stones that can be removed.
---
- ## Example:
> Input: stones = [[0,0],[0,1],[1,0],[1,2],[2,1],[2,2]]
> 
> Output: 5
---
- ## Solution:
**Code :**
```java
class Solution {
    public int removeStones(int[][] stones) {
        int n = stones.length;
        // build graph
        Map<Integer, List<Integer>> map = new HashMap<>();
        for (int [] stone : stones) {
            map.computeIfAbsent(stone[0], x -> new ArrayList<>()).add(~stone[1]);
            map.computeIfAbsent(~stone[1], x -> new ArrayList<>()).add(stone[0]);
        }
        int component = 0;
        Set<Integer> visited = new HashSet<>();
        for (int [] stone : stones) {
            for (int i=0; i<2; i++) {
                int current = i == 0 ? stone[0] : ~stone[1];
                if (!visited.contains(current)) {
                    component += 1;
                    dfs(map, visited, current);
                }
            }
        }
        return n - component;
    }
    
    public void dfs(Map<Integer, List<Integer>> map, Set<Integer> visited, int i) {
        if (visited.contains(i))
            return;
        visited.add(i);
        List<Integer>children = map.get(i);
        for (Integer child : children) {
            if (!visited.contains(child)) {
                dfs(map, visited, child);
            }
        } 
    }
}
