# Longest Common Prefix
---
- ## Question:
> Write a function to find the longest common prefix string amongst an array of strings.
> 
> If there is no common prefix, return an empty string "".
---
- ## Example:
> Input: strs = ["flower","flow","flight"]
> 
> Output: "fl"
---
- ## Solution:
**Code :**
```java
class Solution {
   public String longestCommonPrefix(String[] strs) {
        if (strs == null || strs.length == 0)
            return "";
        
        Arrays.sort(strs);
        String first = strs[0];
        String last = strs[strs.length - 1];
        int c = 0;
        while(c < first.length())
        {
            if (first.charAt(c) == last.charAt(c))
                c++;
            else
                break;
        }
        return c == 0 ? "" : first.substring(0, c);
    }
}
