# Asteroid Collision
---
- ## Question:
> We are given an array asteroids of integers representing asteroids in a row.
> 
> For each asteroid, the absolute value represents its size, and the sign represents its direction (positive meaning right, negative meaning left). Each asteroid moves at the same speed.
> 
> Find out the state of the asteroids after all collisions. If two asteroids meet, the smaller one will explode. If both are the same size, both will explode. Two asteroids moving in the same direction will never meet.
---
- ## Example:
> Input: asteroids = [5,10,-5]
> 
> Output: [5,10]
> 
> Explanation: The 10 and -5 collide resulting in 10. The 5 and 10 never collide.
---
- ## Solution:
**Code :**
```java
class Solution {
    public int[] asteroidCollision(int[] asteroids) {
        Stack<Integer> st=new Stack<>();
        for(int i: asteroids)
        {
            if(i>0)
            {
                st.push(i);
            }
            else
            {
                while(!st.isEmpty() && st.peek()>0 && st.peek()<Math.abs(i))
                {
                    st.pop();
                }
            if(st.isEmpty()||st.peek()<0)
            {
                st.push(i);
            }
            if(st.peek()==Math.abs(i))
            {
                st.pop();
            }
        }
        }
        int[] res=new int[st.size()];
        int j=st.size()-1;
        while(!st.isEmpty())
        {
            res[j--]=st.pop();
        }
        return res;
    }
}
