## 题目地址
n a given grid, each cell can have one of three values:

the value 0 representing an empty cell;
the value 1 representing a fresh orange;
the value 2 representing a rotten orange.
Every minute, any fresh orange that is adjacent (4-directionally) to a rotten orange becomes rotten.

Return the minimum number of minutes that must elapse until no cell has a fresh orange.  If this is impossible, return -1 instead.

 

Example 1:



Input: [[2,1,1],[1,1,0],[0,1,1]]
Output: 4
Example 2:

Input: [[2,1,1],[0,1,1],[1,0,1]]
Output: -1
Explanation:  The orange in the bottom left corner (row 2, column 0) is never rotten, because rotting only happens 4-directionally.
Example 3:

Input: [[0,2]]
Output: 0
Explanation:  Since there are already no fresh oranges at minute 0, the answer is just 0.
 

Note:

1 <= grid.length <= 10
1 <= grid[0].length <= 10
grid[i][j] is only 0, 1, or 2.

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/rotting-oranges
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

## 题目描述

```
n a given grid, each cell can have one of three values:

the value 0 representing an empty cell;
the value 1 representing a fresh orange;
the value 2 representing a rotten orange.
Every minute, any fresh orange that is adjacent (4-directionally) to a rotten orange becomes rotten.

Return the minimum number of minutes that must elapse until no cell has a fresh orange.  If this is impossible, return -1 instead.

 

Example 1:



Input: [[2,1,1],[1,1,0],[0,1,1]]
Output: 4
Example 2:

Input: [[2,1,1],[0,1,1],[1,0,1]]
Output: -1
Explanation:  The orange in the bottom left corner (row 2, column 0) is never rotten, because rotting only happens 4-directionally.
Example 3:

Input: [[0,2]]
Output: 0
Explanation:  Since there are already no fresh oranges at minute 0, the answer is just 0.
 

Note:

1 <= grid.length <= 10
1 <= grid[0].length <= 10
grid[i][j] is only 0, 1, or 2.


```

## 自己的第一遍解法
思路：BFS
```
class Solution:
    def orangesRotting(self, grid: List[List[int]]) -> int:
        minute=0
        L=[]
        num_1=0
        row=len(grid)
        col=len(grid[0])
        for i in range(row):
            for j in range(col):
                if grid[i][j]==2:
                    L.append((i,j))
                elif grid[i][j]==1:
                    num_1+=1
        while L:
            K=L
            L=[]
            for c in K:
                if c[1] >0 and  grid[c[0]][c[1]-1]==1:
                    grid[c[0]][c[1]-1]=2
                    L.append((c[0],c[1]-1))
                if c[1]<col-1 and grid[c[0]][c[1]+1]==1:
                    grid[c[0]][c[1]+1]=2
                    L.append((c[0],c[1]+1))
                if c[0]>0 and grid[c[0]-1][c[1]]==1:
                    grid[c[0]-1][c[1]]=2
                    L.append((c[0]-1,c[1]))
                if c[0]<row-1 and grid[c[0]+1][c[1]]==1:
                    grid[c[0]+1][c[1]]=2
                    L.append((c[0]+1,c[1]))
            num_1-=len(L)
            if L==[]:
                if(num_1==0):
                    return minute
                else:
                    return -1
            minute+=1
        if num_1==0:
            return 0
        return -1

```

## 网上好的解法

* 
```
class Solution(object):
    def orangesRotting(self, grid):
        R, C = len(grid), len(grid[0])

        # queue - all starting cells with rotting oranges
        queue = collections.deque()
        for r, row in enumerate(grid):
            for c, val in enumerate(row):
                if val == 2:
                    queue.append((r, c, 0))

        def neighbors(r, c):
            for nr, nc in ((r-1,c),(r,c-1),(r+1,c),(r,c+1)):
                if 0 <= nr < R and 0 <= nc < C:
                    yield nr, nc

        d = 0
        while queue:
            r, c, d = queue.popleft()
            for nr, nc in neighbors(r, c):
                if grid[nr][nc] == 1:
                    grid[nr][nc] = 2
                    queue.append((nr, nc, d+1))

        if any(1 in row for row in grid):
            return -1
        return d
```
## 对自己的代码的改进
```
while num_1>0 and L:
            legth=len(L)
            for i in range(legth):
                c=L.pop(0)
                if c[1] >0 and  grid[c[0]][c[1]-1]==1:
                    grid[c[0]][c[1]-1]=2
                    L.append((c[0],c[1]-1))
                if c[1]<col-1 and grid[c[0]][c[1]+1]==1:
                    grid[c[0]][c[1]+1]=2
                    L.append((c[0],c[1]+1))
                if c[0]>0 and grid[c[0]-1][c[1]]==1:
                    grid[c[0]-1][c[1]]=2
                    L.append((c[0]-1,c[1]))
                if c[0]<row-1 and grid[c[0]+1][c[1]]==1:
                    grid[c[0]+1][c[1]]=2
                    L.append((c[0]+1,c[1]))
            num_1-=len(L)
            minute+=1
        if num_1>0:
            return -1
        return minute
```
