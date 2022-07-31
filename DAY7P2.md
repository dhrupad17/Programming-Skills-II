# Determine Whether Matrix Can Be Obtained By Rotation
--- 
- ## Question:
> Given two n x n binary matrices mat and target, return true if it is possible to make mat equal to target by rotating mat in 90-degree increments, or false otherwise.
---
- ## Example:
![alt](https://assets.leetcode.com/uploads/2021/05/20/grid3.png)
> Input: mat = [[0,1],[1,0]], target = [[1,0],[0,1]]
> 
> Output: true
> 
> Explanation: We can rotate mat 90 degrees clockwise to make mat equal target.
---
- ## Solution:
**Code :**
```java
class Solution {  
    public boolean findRotation(int[][] mat, int[][] target) {
        int n = mat.length;
        int[] res[] = new int[n][n];
        for (int i = 0; i < n; i++) { //clockwise 90
            for (int j = 0; j < n; j++) {
                res[i][j] = mat[n - 1 - j][i];
            }
        }
        
        int[] res2[] = new int[n][n];
        for (int i = 0; i < n; i++) { //clockwise 180
            for (int j = 0; j < n; j++) {
                res2[i][j] = res[n - 1 - j][i];
            }
        }
       
        int[] res3[] = new int[n][n];
        for (int i = 0; i < n; i++) { //clockwise 270
            for (int j = 0; j < n; j++) {
                res3[i][j] = res2[n - 1 - j][i];
            }
        }
        
		//compare to 90,180,270 and itself
        if(Arrays.deepEquals(target, res) || Arrays.deepEquals(target, res2) || Arrays.deepEquals(target, res3) || Arrays.deepEquals(target, mat) ){ 
            return true;
        }
        return false;
    }
}
