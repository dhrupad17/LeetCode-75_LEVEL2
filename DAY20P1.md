# Combination Sum
---
- ## Question:
> Given an array of distinct integers candidates and a target integer target, return a list of all unique combinations of candidates where the chosen numbers sum to target. You may return the combinations in any order.
> 
> The same number may be chosen from candidates an unlimited number of times. Two combinations are unique if the frequency of at least one of the chosen numbers is different.
> 
> It is guaranteed that the number of unique combinations that sum up to target is less than 150 combinations for the given input.
---
- ## Example:
> Input: candidates = [2,3,6,7], target = 7
> 
> Output: [[2,2,3],[7]]
---
- ## Solution:
**Code :**
```java
class Solution {
    List<List<Integer>> result=new ArrayList<>();
    public List<List<Integer>> combinationSum(int[] arr, int target) {
        gettarget(arr,0,target,new ArrayList<Integer>());
        return result;
    }
    public void gettarget(int[] arr, int position,int currtarget, List<Integer>res)
    {
        //Base Case
        if(currtarget==0)
        {
            result.add(new ArrayList<Integer> (res));
            return;
        }
        if(position==arr.length)
            return;
        if(arr[position]<=currtarget)
        {
            res.add(arr[position]);
            gettarget(arr,position,currtarget-arr[position],res);
            res.remove(res.size()-1);
        }
        gettarget(arr,position+1,currtarget,res);
    }
}
