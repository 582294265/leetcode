## 题目地址
https://leetcode-cn.com/problems/permutations-ii/

## 题目描述

```


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
