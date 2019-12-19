# 63. 不同路径 II
一个机器人位于一个 m x n 网格的左上角 （起始点在下图中标记为“Start” ）。  

机器人每次只能向下或者向右移动一步。机器人试图达到网格的右下角（在下图中标记为“Finish”）。  

现在考虑网格中有障碍物。那么从左上角到右下角将会有多少条不同的路径？  

示例 1:
```
输入:
[
  [0,0,0],
  [0,1,0],
  [0,0,0]
]
输出: 2
解释:
3x3 网格的正中间有一个障碍物。
从左上角到右下角一共有 2 条不同的路径：
1. 向右 -> 向右 -> 向下 -> 向下
2. 向下 -> 向下 -> 向右 -> 向右
```

```go
func uniquePathsWithObstacles(obstacleGrid [][]int) int {
}
```

## 解题思路

## 题解

```go
func uniquePathsWithObstacles(obstacleGrid [][]int) int {

	row := len(obstacleGrid)
	col := len(obstacleGrid[0])

	if row == 0 || col == 0 {
		return 0
	}

	rst := make([][]int, row)
	for i := 0; i < row; i++ {
		rst[i] = make([]int, col)
	}

	for i := 0; i < row; i++ {
		for j := 0; j < col; j++ {

			if obstacleGrid[i][j] == 1 {
				rst[i][j] = 0
			} else {
				if i == 0 && j == 0 {
					rst[i][j] = 1
				} else {
					rst[i][j] = 0
					if i-1 >= 0 {
						rst[i][j] += rst[i-1][j]
					}

					if j-1 >= 0 {
						rst[i][j] += rst[i][j-1]
					}
				}
			}
		}
	}
	return rst[row-1][col-1]
}

```
