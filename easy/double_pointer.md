## 题目地址
https://leetcode-cn.com/problems/he-wei-sde-lian-xu-zheng-shu-xu-lie-lcof/

## 题目描述

```
面试题57 - II. 和为s的连续正数序列
输入一个正整数 target ，输出所有和为 target 的连续正整数序列（至少含有两个数）。

序列内的数字由小到大排列，不同序列按照首个数字从小到大排列。

示例 1：

输入：target = 9
输出：[[2,3,4],[4,5]]
示例 2：

输入：target = 15
输出：[[1,2,3,4,5],[4,5,6],[7,8]]
 

限制：

1 <= target <= 10^5
```

## 自己的第一遍解法
```
class Solution:
    def findContinuousSequence(self, target: int):
        top=target//2
        l=[]
        for x in range(1,top+1):
            temp=-x*x+x-2*target
            d=math.sqrt(1-4*temp)
            if  d%2==1:
                n=int((-1+d)/2)
                l.append([y for y in range(x,n+1)])
        return l
```

## 网上好的解法

* 移动窗口（双指针）
* 求根法（数学）
* 间隔法（对求根法的优化）
[好题要多看]（https://leetcode-cn.com/problems/he-wei-sde-lian-xu-zheng-shu-xu-lie-lcof/solution/xiang-jie-hua-dong-chuang-kou-fa-qiu-gen-fa-jian-g/）
