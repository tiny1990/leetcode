# 110. 平衡二叉树
给定一个二叉树，判断它是否是高度平衡的二叉树。  
本题中，一棵高度平衡二叉树定义为：
> 一个二叉树每个节点 的左右两个子树的高度差的绝对值不超过1。

示例 1:  
给定二叉树 ```[3,9,20,null,null,15,7]```
```
    3
   / \
  9  20
    /  \
   15   7
```
返回 true 。

示例 2:  
给定二叉树 ```[1,2,2,3,3,null,null,4,4]```
```
       1
      / \
     2   2
    / \
   3   3
  / \
 4   4
```
返回 false 。


```go
func isBalanced(root *TreeNode) bool {
}
```

## 解题思路

## 题解

```go
func isBalanced(root *TreeNode) bool {
    return isbalanced(root) != -1
}

func isbalanced(root *TreeNode) int {
    if root == nil {
        return 0
    }

    //divide
    lDepth := isbalanced(root.Left)
    rDepth := isbalanced(root.Right)

    if lDepth == -1 || rDepth == -1 || abs(lDepth - rDepth) > 1 {
        return -1
    }

    //conquer
    return max(lDepth,rDepth) + 1
}

func max(n1, n2 int) int {
    if n1 > n2 {
        return n1
    }
    return n2
}

func abs(n int) int {
    if n < 0 {
        return -n
    }
    return n
}


```
