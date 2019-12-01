# 973. 最接近原点的 K 个点
我们有一个由平面上的点组成的列表 points。需要从中找出 K 个距离原点 (0, 0) 最近的点。  

（这里，平面上两点之间的距离是欧几里德距离。）  

你可以按任何顺序返回答案。除了点坐标的顺序之外，答案确保是唯一的。  

示例 1：
```
输入：points = [[1,3],[-2,2]], K = 1
输出：[[-2,2]]
解释： 
(1, 3) 和原点之间的距离为 sqrt(10)，
(-2, 2) 和原点之间的距离为 sqrt(8)，
由于 sqrt(8) < sqrt(10)，(-2, 2) 离原点更近。
我们只需要距离原点最近的 K = 1 个点，所以答案就是 [[-2,2]]。
```
示例 2：
```
输入：points = [[3,3],[5,-1],[-2,4]], K = 2
输出：[[3,3],[-2,4]]
（答案 [[-2,4],[3,3]] 也会被接受。）
```


```go
func kClosest(points [][]int, K int) [][]int {
}
```

## 解题思路
计算距离 从小到大排序，获取第K个距离  
感觉有个漏洞，如果有相同距离的可能造成返回结果有K + N 个  
应该有计数，当rst 有K个了 可以结束循环


## 题解

```go
func kClosest(points [][]int, K int) [][]int {

    storePath := make([]int,0)
    for _, p := range points {
        path := dist(p[0], p[1])
        storePath = append(storePath, path)
    }

    sort.Ints(storePath)
    max := storePath[K-1]

    rst := make([][]int, 0)

    for _, p := range points {
        path := dist(p[0], p[1])
        if path <= max {
            rst = append(rst, []int{p[0],p[1]})
        }
    }

    return rst
}
func dist(a1, a2 int) int {
    return a1 * a1 + a2 * a2
}
```
