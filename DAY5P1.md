# Longest Palindrome by Concatenating Two Letter Words
---
- ## Question:
> You are given an array of strings words. Each element of words consists of two lowercase English letters.
> 
> Create the longest possible palindrome by selecting some elements from words and concatenating them in any order. Each element can be selected at most once.
> 
> Return the length of the longest palindrome that you can create. If it is impossible to create any palindrome, return 0.
> 
> A palindrome is a string that reads the same forward and backward.
---
- ## Example:
> Input: words = ["lc","cl","gg"]
> 
> Output: 6
---
- ## Solution:
**Code :**
```java
class Solution 
{
    public int longestPalindrome(String[] words) 
    {
        HashMap<String,Integer> map=new HashMap<>();
        int pair=0,sym=0;
        for(String w:words)
        {
            String rev=new StringBuilder(w).reverse().toString();
            if(map.getOrDefault(rev,0)>0)
            {
                ++pair;
                map.put(rev,map.getOrDefault(rev,0)-1);
                if(w.charAt(0)==w.charAt(1))
                    sym--;
            }
            else
            {
                map.put(w,map.getOrDefault(w,0)+1);
                if(w.charAt(0)==w.charAt(1))
                    sym+=1;
            }
        }
        return 4* pair + (sym > 0 ? 2:0);
        
    }
}
