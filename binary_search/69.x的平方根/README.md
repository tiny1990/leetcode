# 69. x 的平方根

实现 int sqrt(int x) 函数。  

计算并返回 x 的平方根，其中 x 是非负整数。  

由于返回类型是整数，结果只保留整数的部分，小数部分将被舍去。  

示例 1:
```
输入: 4
输出: 2
```
示例 2:
```
输入: 8
输出: 2
说明: 8 的平方根是 2.82842..., 
     由于返回类型是整数，小数部分将被舍去。
```


```go
func mySqrt(x int) int {
}
```

## 解题思路
x的平方根，一定在 [1 - x] , 用二分查找

## 题解

```go
func mySqrt(x int) int {

    start := 0
    end := x

    if x <= 0 {
        return 0
    }

    for start + 1 < end {
        mid := start + (end - start ) / 2

        if mid == x / mid {
            return mid
        }
        if mid > x / mid {
            end = mid
        } else {
            start = mid
        }
    }

    return end

}

```
