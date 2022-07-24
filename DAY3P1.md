# Evaluate Reverse Polish Notation
--- 
- ## Question:
> Evaluate the value of an arithmetic expression in Reverse Polish Notation.
> 
> Valid operators are +, -, *, and /. Each operand may be an integer or another expression.
---
- ## Example:
> Input: tokens = ["2","1","+","3","*"]
> 
> Output: 9
> 
> Explanation: ((2 + 1) * 3) = 9
---
- ## Solution:
**Code :**
```java
class Solution {
    public int evalRPN(String[] tokens) {
        Stack<Integer> st=new Stack<>();
        for(String s: tokens)
        {
            switch(s.charAt(s.length()-1))
            {
                case '*':
                    st.push(st.pop()*st.pop());
                    break;
                case '+':
                    st.push(st.pop()+st.pop());
                    break;
                case '-':
                    st.push((-1)*st.pop()+ st.pop());
                    break;
                case '/':
                    int num2=st.pop();
                    int num1=st.pop();
                    st.push(num1/num2);
                    break;
                default:
                    st.push(Integer.valueOf(s));
                    break;
            }
        }
        return st.pop();
    }
}
