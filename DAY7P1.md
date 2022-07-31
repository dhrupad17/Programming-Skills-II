# Rotate Image
--- 
- ## Question:
> You are given an n x n 2D matrix representing an image, rotate the image by 90 degrees (clockwise).
> 
> You have to rotate the image in-place, which means you have to modify the input 2D matrix directly. DO NOT allocate another 2D matrix and do the rotation.
---
- ## Example:
![alt](https://assets.leetcode.com/uploads/2020/08/28/mat1.jpg)
> Input: matrix = [[1,2,3],[4,5,6],[7,8,9]]
> 
> Output: [[7,4,1],[8,5,2],[9,6,3]]
---
- ## Solution:
**Code :**
```java
class Solution {
    public void rotate(int[][] M) {
         for(int i=0;i<(M.length+1)/2;i++)
         {
             for(int j=0;j<(M.length)/2;j++)
             {
                 int temp=M[i][j];
                 M[i][j]=M[M.length-j-1][i];
                 M[M.length-j-1][i]=M[M.length-i-1][M.length-j-1];
                 M[M.length-i-1][M.length-j-1]=M[j][M.length-i-1];
                 M[j][M.length-i-1]=temp;
             }
         }
    }
}
