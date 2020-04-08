## 题目地址
https://leetcode-cn.com/problems/subsets/

## 题目描述

```
Given a set of distinct integers, nums, return all possible subsets (the power set).

Note: The solution set must not contain duplicate subsets.

Example:

Input: nums = [1,2,3]
Output:
[
  [3],
  [1],
  [2],
  [1,2,3],
  [1,3],
  [2,3],
  [1,2],
  []
]


```

## 自己的第一遍解法
> 我利用的是回溯方法

## 网上好的解法
> 利用二进制掩码（第一次见）

```
class Solution:
    def subsets(self, nums: List[int]) -> List[List[int]]:
        n = len(nums)
        output = []
        
        for i in range(2**n, 2**(n + 1)):
            # generate bitmask, from 0..00 to 1..11
            bitmask = bin(i)[3:]
            
            # append subset corresponding to that bitmask
            output.append([nums[j] for j in range(n) if bitmask[j] == '1'])
        
        return output
```
## 关键点
* bitmask = bin(i)[3:] 为什么这样写呢?因为例如bin(3）返回的是ob11
* 再次注意([nums[j] for j in range(n) if bitmask[j] == '1']) python此用法
