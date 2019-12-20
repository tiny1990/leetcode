# 120. 三角形最小路径和
给定一个三角形，找出自顶向下的最小路径和。每一步只能移动到下一行中相邻的结点上。    

例如，给定三角形：
```
[
     [2],
    [3,4],
   [6,5,7],
  [4,1,8,3]
]
自顶向下的最小路径和为 11（即，2 + 3 + 5 + 1 = 11）。
```
说明：
> 如果你可以只使用 O(n) 的额外空间（n 为三角形的总行数）来解决这个问题，那么你的算法会很加分。

```go
func minimumTotal(triangle [][]int) int {
}
```

## 解题思路

## 题解

```go
func minimumTotal(triangle [][]int) int {

    row := len(triangle)
    rst := make([][]int, row)

    for i := 0; i < row; i++ {
        rst[i] = make([]int, len(triangle[i]))
    }

    for i:=0; i < len(triangle[row-1]); i++ {
        rst[row-1][i] = triangle[row-1][i]
    }

    for m := row - 2; m >= 0; m-- {
        for n := 0; n <= m; n++ {
            rst[m][n] = min(rst[m+1][n], rst[m+1][n+1]) + triangle[m][n]
        }
    }

    return rst[0][0]
}

func min(x int, y int) int {
    if x > y {
        return y
    }
    return x
}
```
