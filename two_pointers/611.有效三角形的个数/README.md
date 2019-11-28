# 611. 有效三角形的个数
给定一个包含非负整数的数组，你的任务是统计其中可以组成三角形三条边的三元组个数。  

示例 1:
```
输入: [2,2,3,4]
输出: 3
解释:
有效的组合是: 
2,3,4 (使用第一个 2)
2,3,4 (使用第二个 2)
2,2,3
```
注意:

1. 数组长度不超过1000。
2. 数组里整数的范围为 [0, 1000]。

```go
func triangleNumber(nums []int) int {
}
```

## 解题思路

## 题解

```go
func triangleNumber(nums []int) int {
    
    sort.Ints(nums)
    cnt := 0

    for i:=len(nums) - 1; i >= 2; i-- {
        m,n := 0, i-1

        for m < n {
            if nums[m] + nums[n] > nums[i] {
                cnt += n - m
                n--
            } else {
                m++
            }
        }
    }

    return cnt
}
```
