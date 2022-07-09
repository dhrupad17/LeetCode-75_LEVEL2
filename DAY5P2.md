# Task Scheduler
---
- ## Question:
> Given a characters array tasks, representing the tasks a CPU needs to do, where each letter represents a different task. Tasks could be done in any order. Each task is done in one unit of time. For each unit of time, the CPU could complete either one task or just be idle.
> 
> However, there is a non-negative integer n that represents the cooldown period between two same tasks (the same letter in the array), that is that there must be at least n units of time between any two same tasks.
> 
> Return the least number of units of times that the CPU will take to finish all the given tasks.
---
- ## Example:
> Input: tasks = ["A","A","A","B","B","B"], n = 2
> 
> Output: 8
---
- ## Solution:
**Code :**
```java
class Solution {
    public int leastInterval(char[] tasks, int n) {
        int[] count = new int[26];
        int max = 0;
        int maxCount = 0;
        
        for (char c: tasks){
            count[c-'A']++;
            max = Math.max(count[c-'A'], max);
        }
        
        for (int i: count){
            if (i == max)
                maxCount++;
        }
        
        return Math.max(tasks.length, (max-1) * (n+1) + maxCount);
    }
}
