## 题目地址
https://leetcode-cn.com/problems/power-of-four/

## 题目描述

```
Given an integer (signed 32 bits), write a function to check whether it is a power of 4.

Example 1:

Input: 16
Output: true
Example 2:

Input: 5
Output: false
```

## 自己的第一遍解法
* 没有按照题目要求的不能使用递归和循环解答出

## 网上好的解法
```
//0x5 = 0101b
bool isPowerOfFour(int num) {
    if (num < 0 || num & (num-1)){//check(is or not) a power of 2.
        return false;
    }
    return num & 0x55555555;//check 1 on odd bits
}
```
##  关键点
*  判断一个数是不是2的幂的快速方法 n&n-1 ，因为是2的幂次,只有一个1
*  注意某些语言（如 Java）中，没有无符号整数类型,因此向右移位左边补的是符号位
*  判断是奇是偶 n&&1==1 返回True为奇数
