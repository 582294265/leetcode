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
    def isSubsequence(self, s: str, t: str) -> bool:
        i=0;
        for c  in t:
            if i>=len(s):
                return True
            if s[i]==c:
                i+=1
        if i>=len(s):
            return True
        return False          
  
```

## 网上好的解法

* 利用python3的切片！
```
class Solution:
    def isSubsequence(self, s: str, t: str) -> bool:
        for i in s:
            if t and i in t:
                flag = t.index(i)
                t = t[flag+1:]
            else:
                return False
        return True


```
## 本题主要是思考如何处理很长的字符串T
* 其实很多字符串的问题都可以用桶完成
```
class Solution {
public:
	bool isSubsequence(string s, string t) {
		t.insert(t.begin(), ' ');
		int len1 = s.size(), len2 = t.size();
		
		vector<vector<int> > dp(len2 , vector<int>(26, 0));

		for (char c = 'a'; c <= 'z'; c++) {
			int nextPos = -1; //表示接下来再不会出现该字符

			for (int i = len2 - 1; i>= 0; i--) {  //为了获得下一个字符的位置，要从后往前
				dp[i][c - 'a'] = nextPos;
				if (t[i] == c)
					nextPos = i;
			}
		}

		int index = 0;
		for (char c : s) {
			index = dp[index][c - 'a'];
			if (index == -1)
				return false;
		}
		return true;

	}
};

```
