# 94. 二叉树的中序遍历
给定一个二叉树，返回它的中序 遍历。

示例:
```
输入: [1,null,2,3]
   1
    \
     2
    /
   3

输出: [1,3,2]
```

```go
func inorderTraversal(root *TreeNode) []int {
}
```

## 解题思路
递归,分治

## 题解

### 递归
```go
func inorderTraversal(root *TreeNode) []int {
    
    rst := make([]int,0)
    inorderTravere(root,&rst)
    
    return rst
    
}

func inorderTravere(root *TreeNode, rst *[]int) {
    if root == nil {
        return
    }
    
    inorderTravere(root.Left,rst)
    *rst = append(*rst,root.Val)
    inorderTravere(root.Right,rst)
    
}
```
### 分治
```go
func inorderTraversal(root *TreeNode) []int {
    
    rst := make([]int,0)
    
    if root == nil {
        return rst
    }
    left := inorderTraversal(root.Left)
    right := inorderTraversal(root.Right)
    
    rst = append(rst,left...)
    rst = append(rst,root.Val)
    rst = append(rst,right...)
    
    return rst
}
```