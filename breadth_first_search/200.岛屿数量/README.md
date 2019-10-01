# 200. 岛屿数量
给定一个由 '1'（陆地）和 '0'（水）组成的的二维网格，计算岛屿的数量。一个岛被水包围，并且它是通过水平方向或垂直方向上相邻的陆地连接而成的。你可以假设网格的四个边均被水包围。  
示例 1:
```
输入:
11110
11010
11000
00000

输出: 1
```
示例 2:
```
输入:
11000
11000
00100
00011

输出: 3
```


```go
func numIslands(grid [][]byte) int {
}
```

## 解题思路
标志数组

## 题解

```go
type Coordinate struct {
    x int
    y int
}

func numIslands(grid [][]byte) int {
    
    row := len(grid)
    if row == 0 {
        return 0
    }
    col := len(grid[0])
    count := 0
    
    for i:=0; i < row; i++ {
        for j:=0; j < col; j++ {
            if grid[i][j] == '1' {
                markGrid(i,j,grid)
                count++
            }
        }
    }
    return count
}


func markGrid(x, y int, grid [][]byte) {
    directionX := []int{0,0,-1,1}
    directionY := []int{1,-1,0,0}
    
    grid[x][y] = '0'
    
    queue := make([]*Coordinate,0)
    queue = append(queue,&Coordinate{x,y})
    
    for len(queue) > 0 {
        q := queue[0]
        queue = queue[1:]
        
        for i:=0; i < 4; i++ {
            tmp := &Coordinate{
                x: q.x + directionX[i],
                y: q.y + directionY[i],
            }
            if !inLand(tmp,grid) {
                continue
            }
            if grid[tmp.x][tmp.y] == '1' {
                grid[tmp.x][tmp.y] = '0'
                queue = append(queue,tmp)
            }
        }
    }
}

func inLand(c *Coordinate, grid [][]byte) bool {
    row := len(grid)
    col := len(grid[0])
    
    if c.x >= 0 && c.x < row && c.y < col && c.y >= 0 {
        return true
    }
    return false
}

```
