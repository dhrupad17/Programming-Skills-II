# Repeated Substring Pattern
--- 
- ## Question:
> Given a string s, check if it can be constructed by taking a substring of it and appending multiple copies of the substring together.
---
- ## Example:
> Input: s = "abab"
> 
> Output: true
> 
> Explanation: It is the substring "ab" twice.
---
- ## Solution:
**Code :**
```java
class Solution {
    public boolean repeatedSubstringPattern(String s) {
        String str=s+s;
        return str.substring(1,str.length()-1).contains(s);
    }
}
