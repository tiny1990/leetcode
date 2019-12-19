# 62. 不同路径
一个机器人位于一个 m x n 网格的左上角 （起始点在下图中标记为“Start” ）。

机器人每次只能向下或者向右移动一步。机器人试图达到网格的右下角（在下图中标记为“Finish”）。

问总共有多少条不同的路径？
![pic](./robot_maze.png)

说明：m 和 n 的值均不超过 100。

示例 1:
```
输入: m = 3, n = 2
输出: 3
解释:
从左上角开始，总共有 3 条路径可以到达右下角。
1. 向右 -> 向右 -> 向下
2. 向右 -> 向下 -> 向右
3. 向下 -> 向右 -> 向右
```
示例 2:
```
输入: m = 7, n = 3
输出: 28
```

```go
func uniquePaths(m int, n int) int {
}
```

## 解题思路

## 题解

```go
func uniquePaths(m int, n int) int {
    if m <= 1  || n <= 1 {
        return 1
    }
    rst := make([][]int, m)
    for i := 0; i < m; i++ {
        rst[i] = make([]int, n)
    }

    for i := 0; i < m; i++ {
        for j := 0; j < n; j++ {
            if i == 0 || j == 0 {
                rst[i][j] = 1
            } else {
                rst[i][j] = rst[i-1][j] + rst[i][j-1]
            }
        }
    }
    return rst[m-1][n-1]
}
```
