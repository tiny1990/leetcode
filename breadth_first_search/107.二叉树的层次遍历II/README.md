# 107. 二叉树的层次遍历 II
给定一个二叉树，返回其节点值自底向上的层次遍历。 （即按从叶子节点所在层到根节点所在的层，逐层从左向右遍历）  

例如：  
给定二叉树 ```[3,9,20,null,null,15,7]```,  
```
    3
   / \
  9  20
    /  \
   15   7
```
返回其自底向上的层次遍历为：  
```
[
  [15,7],
  [9,20],
  [3]
]
```

```go
func levelOrderBottom(root *TreeNode) [][]int {
}
```

## 解题思路

## 题解

```go
func levelOrderBottom(root *TreeNode) [][]int {

    rst := make([][]int,0)
    if root == nil {
        return rst
    }
    
    q := make([]*TreeNode,0)
    q = append(q,root)
    
    for len(q) > 0 {
        size := len(q)
        line := make([]int,0)
        
        for i:= 0; i < size; i++ {
            line = append(line,q[0].Val)
                    
            if q[0].Left != nil {
                q = append(q,q[0].Left)
            }
            
            if q[0].Right != nil {
                q = append(q,q[0].Right)
            }
            
            q = q[1:]
        }
        
        rst = append(rst,line)
        
    }
    reverse(rst)
    
    return rst
    
}

func reverse(data [][]int ) {
    for i,j := 0,len(data)-1; i < j; {
        data[i],data[j] = data[j],data[i]
        i++
        j--
    }
}
```
