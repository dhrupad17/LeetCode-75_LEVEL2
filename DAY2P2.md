# Multiply Strings
---
- ## Question:
> Given two non-negative integers num1 and num2 represented as strings, return the product of num1 and num2, also represented as a string.
> 
> Note: You must not use any built-in BigInteger library or convert the inputs to integer directly.
---
- ## Example:
> Input: num1 = "2", num2 = "3"
> 
> Output: "6"
---
- ## Solution:
**Code :**
```java
class Solution {
	public String multiply(String s1, String s2) {
	    java.math.BigInteger a =new java.math.BigInteger(s1);
        java.math.BigInteger b =new java.math.BigInteger(s2);
        b = b.multiply(a);
        return b.toString();
	}

}
