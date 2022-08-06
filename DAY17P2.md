# Lemonade Change
--- 
- ## Question:
> At a lemonade stand, each lemonade costs $5. Customers are standing in a queue to buy from you and order one at a time (in the order specified by bills). Each customer will only buy one lemonade and pay with either a $5, $10, or $20 bill. You must provide the correct change to each customer so that the net transaction is that the customer pays $5.
> 
> Note that you do not have any change in hand at first.
> 
> Given an integer array bills where bills[i] is the bill the ith customer pays, return true if you can provide every customer with the correct change, or false otherwise.
---
- ## Example:
> Input: bills = [5,5,5,10,20]
> 
> Output: true
---
- ## Solution:
**Code :**
```java
class Solution {
    public boolean lemonadeChange(int[] bills) {
        int count5 = 0, count10 = 0;
        for(int p : bills){
            if(p == 5){
                count5++;
            }
            else if(p == 10){
                if(count5 > 0){
                    count5--;
                    count10++;
                }
                else{
                    return false;
                }
            }
            else if(p == 20){
                if(count5 > 0 && count10 > 0){
                    count5--;
                    count10--;
                }
                else if(count5 == 0){
                    return false;
                }
                else if(count5<3){
                    return false;
                }
                else{
                    count5 -= 3;
                }
            }
        }
        return true;
    }
}
