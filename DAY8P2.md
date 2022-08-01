# K Closest Points to Origin
--- 
- ## Question:
> Given an array of points where points[i] = [xi, yi] represents a point on the X-Y plane and an integer k, return the k closest points to the origin (0, 0).
> 
> The distance between two points on the X-Y plane is the Euclidean distance (i.e., √(x1 - x2)2 + (y1 - y2)2).
> 
> You may return the answer in any order. The answer is guaranteed to be unique (except for the order that it is in).
---
- ## Example:
![ALT](https://assets.leetcode.com/uploads/2021/03/03/closestplane1.jpg)
> Input: points = [[1,3],[-2,2]], k = 1
> 
> Output: [[-2,2]]
---
- ## Solution:
**Code :**
```java
class Solution {
    public int[][] kClosest(int[][] points, int k) {
        if(k==points.length)
            return points;
        PriorityQueue<int[]> pq=new PriorityQueue<>(k,new Comparator<int[]>(){
            public int compare(int[] a, int[] b)
            {
                return (b[0]*b[0] + b[1]*b[1])-( a[0]*a[0]+ a[1]*a[1]);
            }
        });
        for(int [] p: points)
        {
            pq.add(p);
            if(pq.size()>k)
            {
                pq.poll();
            }
        }
        return pq.toArray(new int[0][0]);
    }
}
