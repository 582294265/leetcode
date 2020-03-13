## 题目地址
https://leetcode-cn.com/problems/is-subsequence/

## 题目描述

```
392. Is Subsequence
Given a string s and a string t, check if s is subsequence of t.

You may assume that there is only lower case English letters in both s and t. t is potentially a very long (length ~= 500,000) string, and s is a short string (<=100).

A subsequence of a string is a new string which is formed from the original string by deleting some (can be none) of the characters without disturbing the relative positions of the remaining characters. (ie, "ace" is a subsequence of "abcde" while "aec" is not).

Example 1:
s = "abc", t = "ahbgdc"

Return true.

Example 2:
s = "axc", t = "ahbgdc"

Return false.

Follow up:
If there are lots of incoming S, say S1, S2, ... , Sk where k >= 1B, and you want to check one by one to see if T has its subsequence. In this scenario, how would you change your code?

Credits:
Special thanks to @pbrother for adding this problem and creating all test cases.

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
```
