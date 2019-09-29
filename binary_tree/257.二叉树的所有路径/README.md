# 257. 二叉树的所有路径

给定一个二叉树，返回所有从根节点到叶子节点的路径。  

说明: 叶子节点是指没有子节点的节点。  

示例:  
```
输入:

   1
 /   \
2     3
 \
  5

输出: ["1->2->5", "1->3"]

解释: 所有根节点到叶子节点的路径为: 1->2->5, 1->3
```

```go
func binaryTreePaths(root *TreeNode) []string {
}
```

## 解题思路

## 题解

```go
func binaryTreePaths(root *TreeNode) []string {
    
    rst := make([]string,0)
    if root == nil {
        return rst
    }

    if root.Left == nil && root.Right == nil {
        rst = append(rst,fmt.Sprintf("%d",root.Val))
        return rst
    }

    l := binaryTreePaths(root.Left)
    r := binaryTreePaths(root.Right)

    for _, str := range l {
        rst = append(rst,fmt.Sprintf("%d%s%s",root.Val,"->",str))
    }

    for _, str := range r {
        rst = append(rst,fmt.Sprintf("%d%s%s",root.Val,"->",str))
    }

    return rst
}
```
