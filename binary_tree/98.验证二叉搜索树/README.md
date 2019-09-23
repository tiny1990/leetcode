# 98. 验证二叉搜索树
给定一个二叉树，判断其是否是一个有效的二叉搜索树。  
假设一个二叉搜索树具有如下特征：
- 节点的左子树只包含小于当前节点的数。
- 节点的右子树只包含大于当前节点的数。
- 所有左子树和右子树自身必须也是二叉搜索树。

示例 1:  
```
输入:
    2
   / \
  1   3
输出: true
```
示例 2:  
```
输入:
    5
   / \
  1   4
     / \
    3   6
输出: false
解释: 输入为: [5,1,4,null,null,3,6]。
     根节点的值为 5 ，但是其右子节点值为 4 。
```

```go
func isValidBST(root *TreeNode) bool {
}
```

## 解题思路


## 题解

```go
func isValidBST(root *TreeNode) bool {
    
    INT_MAX := int(^uint(0) >> 1)
    INT_MIN := ^INT_MAX
    
    return isValid(root,INT_MIN,INT_MAX) 
    
}

func isValid(root *TreeNode, min int, max int) bool {
    
    if root == nil {
        return true
    }
    if root.Val >= max || root.Val <= min {
        return false
    }
    
    return isValid(root.Left,min,Min(root.Val,max)) && isValid(root.Right,Max(min,root.Val),max)
}

func Max(num1 int, num2 int) int {
    if num1 > num2 {
        return num1
    }
    return num2
}

func Min(num1 int, num2 int) int {
    if num1 < num2 {
        return num1
    }
    return num2
}



```
