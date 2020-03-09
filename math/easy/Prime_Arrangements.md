## 题目地址
https://leetcode-cn.com/problems/prime-arrangements/

## 题目描述

```
1175. Prime Arrangements
Return the number of permutations of 1 to n so that prime numbers are at prime indices (1-indexed.)

(Recall that an integer is prime if and only if it is greater than 1, and cannot be written as a product of two positive integers both smaller than it.)

Since the answer may be large, return the answer modulo 10^9 + 7.

 

Example 1:

Input: n = 5
Output: 12
Explanation: For example [1,2,5,4,3] is a valid permutation, but [5,2,3,4,1] is not because the prime number 5 is at index 1.
Example 2:

Input: n = 100
Output: 682289015
```

## 自己的第一遍解法
```
class Solution:
    def numPrimeArrangements(self, n: int) -> int:
        def is_prime(n):
            if n==1:
                return False
            for i in range(2, int(math.sqrt(n) + 1)):
                if n % i == 0:
                    return False
            return True
        def factorial(number):
            if number <= 1:
                return 1
            else:
                return number*factorial(number-1)
            return True
        i=0
        for c in  range(2,n+1):
            if is_prime(c):
                i+=1
        return factorial(i)*factorial(n-i)% (10**9+7)
```

## 网上好的解法

* 主要是在求素数那进行了优化，这里采用了求素数的一个非常快的方法————厄拉多塞筛法。
```
  public int numPrimeArrangements(int n) {
        int sum = 0;
        if (n > 2){
            sum = fun(n);
        }else {
            return 1;
        }
        long cur = 1L;
        for (int i = 2;i <= sum; i++){
            cur = (cur * i) % (1000000000 + 7);
        }
        for (int i = 2;i <= n - sum; i++){
            cur = (cur * i) % (1000000000 + 7);
        }
        return  (int)cur;
    }

    public int fun (int n){
        n += 1;
        int sum = 0;
        boolean[] bool = new boolean[n+1];
        for (int i = 2;i < n; i++){
            if (bool[i] == false){
                sum ++;
                for (int j = 2; j*i < n; j++) {
                    bool[j*i] = true;
                }
            }
        }
        return sum;
    }
```
## 自己算法的改进
<改进之处在于求素数个数利用了厄拉多塞筛法
```
class Solution:
    def numPrimeArrangements(self, n: int) -> int:
        def fun(n):
            n+=1 #因为计算机中下标从0开始
            bo=[False]*n
            sum=0
            for i in range(2,n):
                if bo[i]==False:
                    sum+=1
                    j=2
                    while j*i<n:
                        bo[j*i]=True
                        j+=1
            return sum
        def factorial(number):
            if number <= 1:
                return 1
            else:
                return number*factorial(number-1)
            return True
        i= fun(n)
        return factorial(i)*factorial(n-i)% (10**9+7)
        
```
