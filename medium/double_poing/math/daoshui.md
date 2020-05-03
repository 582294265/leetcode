## 题目地址
https://leetcode-cn.com/problems/water-and-jug-problem/

## 题目描述

```
365. 水壶问题
有两个容量分别为 x升 和 y升 的水壶以及无限多的水。请判断能否通过使用这两个水壶，从而可以得到恰好 z升 的水？

如果可以，最后请用以上水壶中的一或两个来盛放取得的 z升 水。

你允许：

装满任意一个水壶
清空任意一个水壶
从一个水壶向另外一个水壶倒水，直到装满或者倒空
示例 1: (From the famous "Die Hard" example)

输入: x = 3, y = 5, z = 4
输出: True
示例 2:

输入: x = 2, y = 6, z = 5
输出: False
```

## 自己的第一遍解法
```
无
```

## 网上好的解法

* 主要注意两个break的用法！
```
class Solution:
    def canMeasureWater(self, x: int, y: int, z: int) -> bool:
        if x + y < z:
            return False
        if x == 0 or y == 0:
            return z == 0 or x + y == z
        return z % math.gcd(x, y) == 0
```
* 知识点 贝祖定理 ax+by=z如果有整数解x和y,当且仅当么z是x和y的最大公约数的倍数！
* 本题为什么是ax+by=z，因为不会对一个不满的桶进行加水或者倒水，因为这样做没有意义。可以分情况讨论得出
