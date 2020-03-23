## 题目地址
https://leetcode-cn.com/problems/largest-time-for-given-digits/

## 题目描述

```
Given an array of 4 digits, return the largest 24 hour time that can be made.

The smallest 24 hour time is 00:00, and the largest is 23:59.  Starting from 00:00, a time is larger if more time has elapsed since midnight.

Return the answer as a string of length 5.  If no valid time can be made, return an empty string.

 

Example 1:

Input: [1,2,3,4]
Output: "23:41"
Example 2:

Input: [5,5,5,5]
Output: ""
 

Note:

A.length == 4
0 <= A[i] <= 9



```

## 自己的第一遍解法
**思考许久的题目（一小时）**
```
class Solution:
    def largestTimeFromDigits(self, A) -> str:
        def permutation(end, li, l):
            if 0 == end:
                l.append(li.copy())
            else:
                for i in range(0, end + 1):
                    temp = li[i]
                    li[i] = li[end]
                    li[end] = temp
                    permutation(end - 1, li, l)
                    temp = li[i]
                    li[i] = li[end]
                    li[end] = temp
        length = len(A)
        l = []
        permutation(length - 1, A, l)
        max = -1
        for i in l:
            if i[0] <= 2 and i[2] <= 5:
                hour = i[0] * 10 + i[1]
                minute = i[2] * 10 + i[3]
                if hour <= 23 and minute <= 59:
                    sum = hour * 60 + minute
                    max = sum if max < sum else max
        return "{:02}:{:02}".format(max // 60, max % 60) if max >= 0 else ''
```

## 网上好的解法

**主要是itertools.permutations这个函数不知道**
```
class Solution(object):
    def largestTimeFromDigits(self, A):
        ans = -1
        for h1, h2, m1, m2 in itertools.permutations(A):
            hours = 10 * h1 + h2
            mins = 10 * m1 + m2
            time = 60 * hours + mins
            if 0 <= hours < 24 and 0 <= mins < 60 and time > ans:
                ans = time

        return "{:02}:{:02}".format(*divmod(ans, 60)) if ans >= 0 else ""
```
