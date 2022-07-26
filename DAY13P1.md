# Range Sum Query 2D - Immutable
--- 
- ## Question:
> Given a 2D matrix matrix, handle multiple queries of the following type:
> 
> Calculate the sum of the elements of matrix inside the rectangle defined by its upper left corner (row1, col1) and lower right corner (row2, col2).
> 
> Implement the NumMatrix class:
> 
>- NumMatrix(int[][] matrix) Initializes the object with the integer matrix matrix.
>- int sumRegion(int row1, int col1, int row2, int col2) Returns the sum of the elements of matrix inside the rectangle defined by its upper left corner (row1, col1) and lower right corner (row2, col2).
> You must design an algorithm where sumRegion works on O(1) time complexity.
---
- ## Example:
![ALT](https://assets.leetcode.com/uploads/2021/03/14/sum-grid.jpg)
> Input
["NumMatrix", "sumRegion", "sumRegion", "sumRegion"]
[[[[3, 0, 1, 4, 2], [5, 6, 3, 2, 1], [1, 2, 0, 1, 5], [4, 1, 0, 1, 7], [1, 0, 3, 0, 5]]], [2, 1, 4, 3], [1, 1, 2, 2], [1, 2, 2, 4]]

> Output
[null, 8, 11, 12]
---
- ## Solution:
**Code :**
```java
class NumMatrix {
    long[][] dp;
    
    public NumMatrix(int[][] M) {
        int ylen = M.length + 1, xlen = M[0].length + 1;
        dp = new long[ylen][xlen];
        for (int i = 1; i < ylen; i++)
            for (int j = 1; j < xlen; j++)
                dp[i][j] = M[i-1][j-1] + dp[i-1][j] + dp[i][j-1] - dp[i-1][j-1];
    }
    
    public int sumRegion(int R1, int C1, int R2, int C2) {
        return (int)(dp[R2+1][C2+1] - dp[R2+1][C1] - dp[R1][C2+1] + dp[R1][C1]);
    }
}
