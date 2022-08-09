# Design Authentication Manager
--- 
- ## Question:
> There is an authentication system that works with authentication tokens. For each session, the user will receive a new authentication token that will expire timeToLive seconds after the currentTime. If the token is renewed, the expiry time will be extended to expire timeToLive seconds after the (potentially different) currentTime.
---
- ## Example:
![ALT](https://assets.leetcode.com/uploads/2021/02/25/copy-of-pc68_q2.png)
> Input
["AuthenticationManager", "renew", "generate", "countUnexpiredTokens", "generate", "renew", "renew", "countUnexpiredTokens"]
[[5], ["aaa", 1], ["aaa", 2], [6], ["bbb", 7], ["aaa", 8], ["bbb", 10], [15]]
>
> Output
[null, null, null, 1, null, null, null, 0]
---
- ## Solution:
**Code :**
```java
class AuthenticationManager {
    private int ttl;
    private Map<String, Integer> map;

    public AuthenticationManager(int timeToLive) {
        this.ttl = timeToLive;
        this.map = new HashMap<>();
    }
    
    public void generate(String tokenId, int currentTime) {
        map.put(tokenId, currentTime + this.ttl);
    }
    
    public void renew(String tokenId, int currentTime) {
        Integer expirationTime = this.map.getOrDefault(tokenId, null);
        if (expirationTime == null || expirationTime <= currentTime)
            return;
        
        generate(tokenId, currentTime);
    }
    
    public int countUnexpiredTokens(int currentTime) {
        int count = 0;
        for (Map.Entry<String, Integer> entry: this.map.entrySet())
            if (entry.getValue() > currentTime)
                count++;
        
        return count;
    }
}
