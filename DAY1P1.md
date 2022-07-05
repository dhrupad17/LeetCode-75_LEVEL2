# Happy Number
---
- ## Question:
> Write an algorithm to determine if a number n is happy.
> 
> A happy number is a number defined by the following process:
> 
>- Starting with any positive integer, replace the number by the sum of the squares of its digits.
>- Repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1.
>- Those numbers for which this process ends in 1 are happy.
>
> Return true if n is a happy number, and false if not.
---
- ## Example:
> Input: n = 19
> 
> Output: true
---
- ## Solution:
**Code :**
```java
class Solution {
    public boolean isHappy(int n) {
        if(n<=0)
            return false;
        
        while(true)
        {
            int sum=0;
            while(n!=0)
            {
            // int sum=0;
            sum=sum+(n%10)*(n%10);
            n=n/10;
            }
            if(sum/10==0)
            {
                if(sum==1||sum==7)
                    return true;
                else
                    return false;
            }
        n=sum;
    }
}
}
