# 114. 二叉树展开为链表
给定一个二叉树，原地将它展开为链表。  

例如，给定二叉树  

```
    1
   / \
  2   5
 / \   \
3   4   6
```
将其展开为：
```
1
 \
  2
   \
    3
     \
      4
       \
        5
         \
          6
```

```go
func flatten(root *TreeNode)  {
}
```

## 解题思路
// divide conquer

## 题解

```go
func flatten(root *TreeNode)  {
    helper(root)
}

func helper(root *TreeNode) *TreeNode {

    if root == nil {
        return nil
    }

    lNode := helper(root.Left)
    rNode := helper(root.Right)

    if lNode != nil {
        lNode.Right = root.Right
        root.Right = root.Left
        root.Left = nil
    }

    if rNode != nil {
        return rNode
    }

    if lNode != nil {
        return lNode
    }
    
    return root
}

```
