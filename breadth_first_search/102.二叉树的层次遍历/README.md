# 102. 二叉树的层次遍历
给定一个二叉树，返回其按层次遍历的节点值。 （即逐层地，从左到右访问所有节点）。  

例如:
给定二叉树: ```[3,9,20,null,null,15,7]```,
```
    3
   / \
  9  20
    /  \
   15   7
```
返回其层次遍历结果：
```
[
  [3],
  [9,20],
  [15,7]
]
```


```go
func levelOrder(root *TreeNode) [][]int {
}
```

## 解题思路

## 题解

```go
func levelOrder(root *TreeNode) [][]int {

    rst := make([][]int,0)
    if root == nil {
        return rst
    }

    queue := make([]*TreeNode,0)
    queue = append(queue,root)

    for len(queue) > 0 {
        size := len(queue)
        row := make([]int,0)
        
        for i:=0; i < size; i++ {
            node := queue[0]
            row = append(row,node.Val)
            if node.Left != nil {
                queue = append(queue,node.Left)
            }
            if node.Right != nil {
                queue = append(queue,node.Right)
            }
            queue = queue[1:]
        }
        
        rst = append(rst,row)
    }
    return rst
}
```
