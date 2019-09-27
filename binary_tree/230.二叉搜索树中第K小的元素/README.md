# 230. 二叉搜索树中第K小的元素
给定一个二叉搜索树，编写一个函数 kthSmallest 来查找其中第 k 个最小的元素。  

说明：  
你可以假设 k 总是有效的，1 ≤ k ≤ 二叉搜索树元素个数。  

示例 1:
```
输入: root = [3,1,4,null,2], k = 1
   3
  / \
 1   4
  \
   2
输出: 1
```
示例 2:
```
输入: root = [5,3,6,2,4,null,null,1], k = 3
       5
      / \
     3   6
    / \
   2   4
  /
 1
输出: 3
```

```go
func kthSmallest(root *TreeNode, k int) int {
}
```

## 解题思路
中序遍历的变种

## 题解

```go
func kthSmallest(root *TreeNode, k int) int {

    var count, rst int
    helper(root,k,&count,&rst)
    return rst
}

func helper(root *TreeNode, k int, count *int, n *int) {

    if root == nil {
        return 
    }

    helper(root.Left, k, count, n)
    *count++

    if *count == k {
        *n = root.Val
        return
    }
    helper(root.Right, k, count, n)
}

```
