# Minimum Window Substring
---
- ## Question:
> Given two strings s and t of lengths m and n respectively, return the minimum window substring of s such that every character in t (including duplicates) is included in the window. If there is no such substring, return the empty string "".
>
> The testcases will be generated such that the answer is unique.
>
> A substring is a contiguous sequence of characters within the string.
---
- ## Example:
> Input: s = "ADOBECODEBANC", t = "ABC"
> 
> Output: "BANC"
> 
> Explanation: The minimum window substring "BANC" includes 'A', 'B', and 'C' from string t.
---
- ## Solution:
**Code :**
```java
class Solution {
    public String minWindow(String s, String t) {
        HashMap<Character,Integer> map = new HashMap<>();
        for(int i = 0; i < t.length(); i++){
            map.put(t.charAt(i),map.getOrDefault(t.charAt(i),0)+1);
        }
        int i = 0;
        int j = 0;
        int count = map.size();
        int minimumI = 0;
        int minimumJ = 0;
        int minimum = Integer.MAX_VALUE;

        while(j < s.length()) {

            if (map.containsKey(s.charAt(j))) {
                map.put(s.charAt(j), map.get(s.charAt(j)) - 1);
                if (map.get(s.charAt(j)) == 0) {
                    count--;
                }
            }
            if (count > 0) {
                j++;
            }
            else{
                while (count == 0) {
                    if (minimum > j - i + 1) {
                        minimum = j - i + 1;
                        minimumI = i;
                        minimumJ = j + 1;
                    }
                    if(map.containsKey(s.charAt(i))){
                        map.put(s.charAt(i), map.get(s.charAt(i)) + 1);
                        if(map.get(s.charAt(i))== 1){
                          count++;
                        }
                    }
                    i++;
                }
                j++;
            }
        }
        return s.substring(minimumI,minimumJ);
    }
}
