# Add Binary
--- 
- ## Question:
> Given two binary strings a and b, return their sum as a binary string.
---
- ## Example:
> Input: a = "11", b = "1"
> 
> Output: "100"
---
- ## Solution:
**Code :**
```java
class Solution {
    public String addBinary(String a, String b) {
         java.math.BigInteger n1=new java.math.BigInteger(a,2);
        java.math.BigInteger n2=new java.math.BigInteger(b,2);
        
        n1=n1.add(n2);
        return n1.toString(2);
    }
}
