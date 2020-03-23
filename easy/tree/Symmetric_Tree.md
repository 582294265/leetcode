## 题目地址
https://leetcode-cn.com/problems/symmetric-tree/

## 题目描述

```
Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).

For example, this binary tree [1,2,2,3,4,4,3] is symmetric:

    1
   / \
  2   2
 / \ / \
3  4 4  3
 

But the following [1,2,2,null,3,null,3] is not:

    1
   / \
  2   2
   \   \
   3    3
 

Note:
Bonus points if you could solve it both recursively and iteratively.


```

## 自己的第一遍解法
```
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
def xianxu(p,L):
    if p==None:
        L.append(p)
    else:
        xianxu(p.left,L)
        xianxu(p.right,L)
        L.append(p.val)
def houxu(p,L):
    if p==None:
        L.append(p)
    else:
        houxu(p.right,L)
        houxu(p.left,L)
        L.append(p.val)

class Solution:
    def isSymmetric(self, root: TreeNode) -> bool:
        L1=[]
        L2=[]
        xianxu(root,L1)
        houxu(root,L2)
        print(L1)
        print(L2)
        return L1==L2
```

## 网上好的解法
* 方式一
```
public boolean isSymmetric(TreeNode root) {
    return isMirror(root, root);
}

public boolean isMirror(TreeNode t1, TreeNode t2) {
    if (t1 == null && t2 == null) return true;
    if (t1 == null || t2 == null) return false;
    return (t1.val == t2.val)
        && isMirror(t1.right, t2.left)
        && isMirror(t1.left, t2.right);
}
```
* 方式二
```
public boolean isSymmetric(TreeNode root) {
    Queue<TreeNode> q = new LinkedList<>();
    q.add(root);
    q.add(root);
    while (!q.isEmpty()) {
        TreeNode t1 = q.poll();
        TreeNode t2 = q.poll();
        if (t1 == null && t2 == null) continue;
        if (t1 == null || t2 == null) return false;
        if (t1.val != t2.val) return false;
        q.add(t1.left);
        q.add(t2.right);
        q.add(t1.right);
        q.add(t2.left);
    }
    return true;
}
```
## 收获
* [python中队列的用法](https://www.geeksforgeeks.org/queue-in-python/) ,如果是用列表，pop(0)是关键
