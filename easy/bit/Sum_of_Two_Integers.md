## 题目地址
https://leetcode-cn.com/problems/sum-of-two-integers/

## 题目描述

```
Calculate the sum of two integers a and b, but you are not allowed to use the operator + and -.

Example 1:

Input: a = 1, b = 2
Output: 3
Example 2:

Input: a = -2, b = 3
Output: 1

```

## 自己的第一遍解法

> 没有做出


## 网上好的解法

```
class Solution {
    public int getSum(int a, int b) {
        int temp=0;
        while (b!=0){
            temp= a^b;
            b=(a&b)<<1;
            a=temp;
        }
        return a;
    }
}
```
* 知识点: 计算机底层相加运用异或,进位是相与。
