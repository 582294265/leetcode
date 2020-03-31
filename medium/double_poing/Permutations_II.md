## 题目地址
https://leetcode-cn.com/problems/permutations-ii/

## 题目描述

```
给定一个可包含重复数字的序列，返回所有不重复的全排列。

示例:

输入: [1,1,2]
输出:
[
  [1,1,2],
  [1,2,1],
  [2,1,1]
]


```

## 自己的第一遍解法
* 没有通过反例 01009  ,原因是换来换去的递归过程中，后半部分不连续了
```
class Solution:
    def permuteUnique(self, nums: List[int]) -> List[List[int]]:
        def p(nums,start,end,l):
            if start==end:
                l.append(nums[:])
            else:
                for i in range(start,end+1):
                    if i!=start and nums[i]==nums[i-1]:
                        continue
                    nums[i],nums[start]=nums[start],nums[i]
                    p(nums.copy(),start+1,end,l)
                    nums[i],nums[start]=nums[start],nums[i]
                       
        K=[]
        nums.sort()
        p(nums,0,len(nums)-1,K)
        return K
```


## 网上好的解法
*  关键点在于回溯和截枝
*  本题能够实现截枝的关键设立了used数组！！！ 好好阅读
```
from typing import List


class Solution:

    def permuteUnique(self, nums: List[int]) -> List[List[int]]:

        def dfs(nums, size, depth, path, used, res):
            if depth == size:
                res.append(path.copy())
                return
            for i in range(size):
                if not used[i]:

                    if i > 0 and nums[i] == nums[i - 1] and not used[i - 1]:
                        continue

                    used[i] = True
                    path.append(nums[i])
                    dfs(nums, size, depth + 1, path, used, res)
                    used[i] = False
                    path.pop()

        size = len(nums)
        if size == 0:
            return []

        nums.sort()

        used = [False] * len(nums)
        res = []
        dfs(nums, size, 0, [], used, res)
        return res

```
## 后来又有一条好的做法
* 一定要先排序
```
class Solution:
    def permuteUnique(self, nums: List[int]) -> List[List[int]]:
        def p(nums,start,end,l):
            if start==end:
                l.append(nums[:])
            else:
                for i in range(start,end+1):
                    if i!=start and nums[i]==nums[start]:
                        continue
                    nums[i],nums[start]=nums[start],nums[i]
                    p(nums.copy(),start+1,end,l)
                   
                       
        K=[]
        nums.sort()
        p(nums,0,len(nums)-1,K)
        return K
```
