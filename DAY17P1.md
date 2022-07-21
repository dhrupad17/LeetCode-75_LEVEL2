# Insert Interval
---
- ## Question:
> You are given an array of non-overlapping intervals intervals where intervals[i] = [starti, endi] represent the start and the end of the ith interval and intervals is sorted in ascending order by starti. You are also given an interval newInterval = [start, end] that represents the start and end of another interval.
> 
> Insert newInterval into intervals such that intervals is still sorted in ascending order by starti and intervals still does not have any overlapping intervals (merge overlapping intervals if necessary).
> 
> Return intervals after the insertion.
---
- ## Example:
> Input: intervals = [[1,3],[6,9]], newInterval = [2,5]
> 
> Output: [[1,5],[6,9]]
---
- ## Solution:
**Code :**
```java
class Solution {
    public int[][] insert(int[][] intervals, int[] newInterval) {
         List<int[]> result = new ArrayList<>();
        
        // Iterate through all slots
        for(int[] slot : intervals)
        {
            
            // if newInterval before slot insert newInterval & update slot as new interval
            if(newInterval[1] < slot[0])
            {
                result.add(newInterval);
                newInterval = slot;
            } 
            
            // if slot is lesser than new Interval insert slot
            else if(slot[1] < newInterval[0])
            {
                result.add(slot);
            } 
            
            // if above conditions fail its an overlap since possibility of new interval existing in left & right of slot is checked
            // update lowest of start & highest of end & not insert
            else {
                newInterval[0] = Math.min(newInterval[0],slot[0]);
                newInterval[1] = Math.max(newInterval[1],slot[1]);
            }
        }
        
        // insert the last newInterval
        result.add(newInterval);
        
        // convert to int[][] array
        return result.toArray(new int[result.size()][]);
    }
}
