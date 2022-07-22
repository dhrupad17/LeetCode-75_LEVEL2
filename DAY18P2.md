# Basic Calculator II
---
- ## Question:
> Given a string s which represents an expression, evaluate this expression and return its value. 
> 
> The integer division should truncate toward zero.
> 
>
>You may assume that the given expression is always valid. All intermediate results will be in the range of [-231, 231 - 1].
>
> Note: You are not allowed to use any built-in function which evaluates strings as mathematical expressions, such as eval().
---
- ## Example:
> Input: s = "3+2*2"
> 
> Output: 7
---
- ## Solution:
**Code :**
```java
public class Solution {
    public int calculate(String s) {
        if(s == null || s.length() == 0)
            return 0;
        boolean divide = false;
        int result = 0, sign = 1, num = 0, preNum = 0;
        for(char c: s.toCharArray()) {
            if(c >= '0' && c <= '9')
                num = num * 10 + c -'0';
            else if(c == '+' || c == '-' || c == '*' || c == '/') {
                if(divide) {
                    num = preNum/num;
                    divide = false;
                }
                //record the temp result, think about case 2 * 5 / 2
                if(c == '/') {
                    divide = true;
                    preNum = num * sign;
                    sign = 1;
                } else if(c == '*'){
                    sign *= num;
                } else {
                    result += sign * num;
                    sign = c == '+' ? 1 : -1;
                }
                num = 0;
            }
        }
        if(num > 0) {
            if(divide)
                num = preNum/num;
            result += sign * num;
        }
        return result;
    }
}
