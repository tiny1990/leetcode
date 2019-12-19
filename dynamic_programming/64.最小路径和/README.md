# 64. 最小路径和
给定一个包含非负整数的 m x n 网格，请找出一条从左上角到右下角的路径，使得路径上的数字总和为最小。  

说明：每次只能向下或者向右移动一步。  

示例:
```
输入:
[
  [1,3,1],
  [1,5,1],
  [4,2,1]
]
输出: 7
解释: 因为路径 1→3→1→1→1 的总和最小。
```

```go
func minPathSum(grid [][]int) int {
}
```

## 解题思路

## 题解

```go
func minPathSum(grid [][]int) int {
    // 初始化
    rst := make([][]int,len(grid))
    for i:=0; i< len(grid); i++ {
        rst[i] = make([]int,len(grid[0]))
    }
    
    rst[0][0] = grid[0][0]
    // init row
    for i:=1; i<len(grid); i++ {
        rst[i][0] = rst[i-1][0] + grid[i][0]
    }

    for i:=1; i<len(grid[0]); i++ {
        rst[0][i] = rst[0][i-1] + grid[0][i]
    }
    for i:=1; i<len(grid); i++ {
        for j:=1; j<len(grid[i]); j++ {
            rst[i][j] = min(rst[i-1][j], rst[i][j-1]) + grid[i][j]
        }
    }
    return rst[len(grid)-1][len(grid[0])-1]
}
func min(m,n int) int {
    
    if m>n {
        return n
    }
    return m
}
```
