## 题目地址
https://leetcode-cn.com/problems/climbing-stairs/

## 题目描述

```
70. Climbing Stairs
You are climbing a stair case. It takes n steps to reach to the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

Note: Given n will be a positive integer.

Example 1:

Input: 2
Output: 2
Explanation: There are two ways to climb to the top.
1. 1 step + 1 step
2. 2 steps
Example 2:

Input: 3
Output: 3
Explanation: There are three ways to climb to the top.
1. 1 step + 1 step + 1 step
2. 1 step + 2 steps
3. 2 steps + 1 step

```

## 自己的第一遍解法
> 未解答出
## 网上好的解法
[爬楼题解答六种方式都要会！](https://leetcode-cn.com/problems/climbing-stairs/)
## 收获（此题好好研究收获很大）
* n &1 如果结果为1说明是奇数，如果是0则是偶数 
* 快速求幂方法要掌握 [基础的快速求幂方法教学]（https://www.jianshu.com/p/25eba927d9da）
* 斐波那契数列可以求个表达式，利用你组合数学学过母函数方法（重要）!
* 递归树，如果有相同重复的部分，可以添加个temp数组，用于记录，就如方式二一样


