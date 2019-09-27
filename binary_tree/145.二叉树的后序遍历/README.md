# 145. 二叉树的后序遍历
给定一个二叉树，返回它的 后序 遍历。  

示例:
```
输入: [1,null,2,3]  
   1
    \
     2
    /
   3 

输出: [3,2,1]
```

```go
func postorderTraversal(root *TreeNode) []int {
}
```

## 解题思路

## 题解

```go
func postorderTraversal(root *TreeNode) []int {
    
    rst := make([]int,0)
    
    if root == nil {
        return rst
    }
    
    left := postorderTraversal(root.Left)
    right := postorderTraversal(root.Right)
    
    rst = append(rst,left...)
    rst = append(rst,right...)
    rst = append(rst,root.Val)

    return rst
    
}
```
