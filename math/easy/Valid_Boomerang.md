## 题目地址
https://leetcode-cn.com/problems/valid-boomerang/

## 题目描述

```
A boomerang is a set of 3 points that are all distinct and not in a straight line.

Given a list of three points in the plane, return whether these points are a boomerang.

 

Example 1:

Input: [[1,1],[2,3],[3,2]]
Output: true
Example 2:

Input: [[1,1],[2,2],[3,3]]
Output: false
 

Note:

points.length == 3
points[i].length == 2
0 <= points[i][j] <= 100

```

## 自己的第一遍解法
```
class Solution:
    def isBoomerang(self, points: List[List[int]]) -> bool:
        if points[0][0] == points[1][0] == points[2][0]:
            return False
        a, b, c = points[0], points[1], points[2]
        if a==b or a==c:
            return False
        d1 = b[0] - a[0]
        if d1 == 0:
            return True
        k1 = (b[1] - a[1]) / d1
        d2 = c[0] - a[0]
        if d2 == 0:
            return True
        k2 = (c[1] - a[1]) / d2
        return k1 != k2
```

## 网上好的解法
**方法一,利用了三角形的计算公式
这是已知三角形3顶点坐标A（x1,y1），B（x2,y2），C（x3,y3），求三角形ABC的面积的公式
公式中书写形式是二阶行列式
写成一般形式如下：
设A（x1,y1），B（x2,y2），C（x3,y3）在坐标系中中顺序为三点按逆时针排列
S=1/2[(x1y2-x2y1)+(x2y3-x3y2)+(x3y1-x1y3)]
已知三角形3顶点坐标，求三角形面积最直接的公式**
```
class Solution {
    public boolean isBoomerang(int[][] p) {
        
        return (p[0][0] * (p[1][1] - p[2][1]) + p[1][0] * (p[2][1] - p[0][1]) + p[2][0] * (p[0][1] - p[1][1])) != 0;
    }
}
```

**
方法二，在我方法上进行了改进 b/a=d/c为了不考虑 a和c是否为0 ，利用是否ad=bc！
**

```
bool isBoomerang(int** points, int pointsSize, int* pointsColSize){
    int x1 = points[0][0] - points[1][0];
    int y1 = points[0][1] - points[1][1];
    
    int x2 = points[0][0] - points[2][0];
    int y2 = points[0][1] - points[2][1];
    
    return x1 * y2 != x2 * y1;
}
```
