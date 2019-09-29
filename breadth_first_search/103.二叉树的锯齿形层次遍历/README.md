# 103. 二叉树的锯齿形层次遍历
给定一个二叉树，返回其节点值的锯齿形层次遍历。（即先从左往右，再从右往左进行下一层遍历，以此类推，层与层之间交替进行）。
例如：  
给定二叉树 ```[3,9,20,null,null,15,7]```,
```
    3
   / \
  9  20
    /  \
   15   7
```
返回锯齿形层次遍历如下：  
```
[
  [3],
  [20,9],
  [15,7]
]
```


```go
func zigzagLevelOrder(root *TreeNode) [][]int {
}
```

## 解题思路

## 题解

```go
func zigzagLevelOrder(root *TreeNode) [][]int {
    
    rst := make([][]int,0)
    
    if root == nil {
        return rst
    }
    
    queue := make([]*TreeNode,0)
    queue = append(queue,root)
    
    count := 0
    for len(queue) > 0 {
        size := len(queue)
        row := make([]int,0)
        
        count++
        for i := 0; i < size; i++ {
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
        if count % 2 == 0 {
            reverse(row) 
        }
        
        rst = append(rst,row)
    }
    return rst
}

func reverse(array []int) {
    i := 0
    j := len(array) - 1
    
    for i < j {
        array[i],array[j] = array[j],array[i]
        i++
        j--
    }
}
```
