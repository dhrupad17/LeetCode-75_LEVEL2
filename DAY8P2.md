# Search in Rotated Sorted Array
---
- ## Question:
> There is an integer array nums sorted in ascending order (with distinct values).
> 
> Prior to being passed to your function, nums is possibly rotated at an unknown pivot index k (1 <= k < nums.length) such that the resulting array is [nums[k], nums[k+1], ..., nums[n-1], nums[0], nums[1], ..., nums[k-1]] (0-indexed). For example, [0,1,2,4,5,6,7] might be rotated at pivot index 3 and become [4,5,6,7,0,1,2].
> 
> Given the array nums after the possible rotation and an integer target, return the index of target if it is in nums, or -1 if it is not in nums.
> 
> You must write an algorithm with O(log n) runtime complexity.
---
- ## Example:
> Input: nums = [4,5,6,7,0,1,2], target = 0
> 
> Output: 4
---
- ## Solution:
**Code :**
```java
class Solution {
    public int search(int[] arr, int target) {
        int p=pivot(arr);
        if(p==-1)
        {
            return bs(arr,target,0,arr.length-1);
        }
        if(arr[p]==target)
            return p;
        if(target>=arr[0])
            return bs(arr,target,0,p-1);
        // if(target<arr[0])
        return bs(arr,target,p+1,arr.length-1);
    }
    public int pivot(int arr[])
    {
        int start=0;
        int end=arr.length-1;
        while(start<=end)
        {
            int mid=start+(end-start)/2;
            if(mid<end && arr[mid]>arr[mid+1])
            {
                return mid;
            }
            if(mid>start && arr[mid]<arr[mid-1])
            {
                return mid-1;
            }
            if(arr[mid]<=arr[start])
            {
                end=mid-1;
            }
            else
            {
                start=mid+1;
            }
        }
        return -1;
    }
    public int bs(int[] arr,int target, int start, int end)
    {
        while(start<=end)
        {
            int mid=start+(end-start)/2;
            if(arr[mid]>target)
            {
                end=mid-1;
            }
            else if(arr[mid]<target)
            {
                start=mid+1;
            }
            else
            {
                return mid;
            }
        }
        return -1;
    }
}
