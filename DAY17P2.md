# Merge Intervals
---
- ## Question:
> Given an array of intervals where intervals[i] = [starti, endi], merge all overlapping intervals, and return an array of the non-overlapping intervals that cover all the intervals in the input.
---
- ## Example:
> Input: intervals = [[1,3],[2,6],[8,10],[15,18]]
> 
> Output: [[1,6],[8,10],[15,18]]
> 
> Explanation: Since intervals [1,3] and [2,6] overlap, merge them into [1,6].
---
- ## Solution:
**Code :**
```java
class Solution {
    public int[][] merge(int[][] intervals) {
        List<int[]> ans=new ArrayList<>();
        if(intervals!=null || intervals.length!=0)
        {
            Arrays.sort(intervals,(a,b)-> a[0]-b[0]);
            int start=intervals[0][0];
            int end=intervals[0][1];
            for(int i[]: intervals)
            {
                if(i[0]<=end)
                {
                    end=Math.max(end,i[1]);
                }
                else
                {
                    ans.add(new int[]{start,end});
                    start=i[0];
                    end=i[1];
                }
            }
            ans.add(new int[]{start,end});
        }
        return ans.toArray(new int[0][]);
    }
}
