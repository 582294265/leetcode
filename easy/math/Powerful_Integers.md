## 题目地址
https://leetcode-cn.com/problems/powerful-integers/

## 题目描述

```
Given two positive integers x and y, an integer is powerful if it is equal to x^i + y^j for some integers i >= 0 and j >= 0.

Return a list of all powerful integers that have value less than or equal to bound.

You may return the answer in any order.  In your answer, each value should occur at most once.

 

Example 1:

Input: x = 2, y = 3, bound = 10
Output: [2,3,4,5,7,9,10]
Explanation: 
2 = 2^0 + 3^0
3 = 2^1 + 3^0
4 = 2^0 + 3^1
5 = 2^1 + 3^1
7 = 2^2 + 3^1
9 = 2^3 + 3^0
10 = 2^0 + 3^2
Example 2:

Input: x = 3, y = 5, bound = 15
Output: [2,4,6,8,10,14]
 

Note:

1 <= x <= 100
1 <= y <= 100
0 <= bound <= 10^6

```

## 自己的第一遍解法
```
class Solution:
    def powerfulIntegers(self, x: int, y: int, bound: int) -> List[int]: 
        s=set()
        for i in range(0,20):
            a=x**i
            if(a>bound):
                break;
            for j in range(0,20):
                b=y**j
                if (a+b<=bound):
                    s.add(a+b)
        return s 
```

## 网上好的解法

* 主要注意两个break的用法！
```
class Solution {
    public List<Integer> powerfulIntegers(int x, int y, int bound) {
        Set<Integer> set = new HashSet<>();
        
        for (int a = 1; a < bound; a *= x) {
            for (int b = 1; a + b <= bound; b *= y) {
                set.add(a + b);
                if (y == 1) break;
            }
            if (x == 1) break;
        }
        
        return new ArrayList<>(set);
    }
}
