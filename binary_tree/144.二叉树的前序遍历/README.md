# 144. 二叉树的前序遍历
给定一个二叉树，返回它的 前序 遍历。  

示例:
```
输入: [1,null,2,3]  
   1
    \
     2
    /
   3 

输出: [1,2,3]
```


```go
func preorderTraversal(root *TreeNode) []int {
}
```

## 解题思路
分治法

## 题解

```go
// divide conquer
func preorderTraversal(root *TreeNode) []int {

    rst := make([]int,0)
    if root == nil {
        return rst
    }
    
    //divide
    left := preorderTraversal(root.Left)
    right := preorderTraversal(root.Right)
    
    // conquer
    rst = append(rst,root.Val)
    rst = append(rst,left...)
    rst = append(rst,right...)
    
    return rst
}

```
