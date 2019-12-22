# 300. 最长上升子序列
给定一个无序的整数数组，找到其中最长上升子序列的长度。  

示例:
```
输入: [10,9,2,5,3,7,101,18]
输出: 4 
解释: 最长的上升子序列是 [2,3,7,101]，它的长度是 4。
```
说明:  
- 可能会有多种最长上升子序列的组合，你只需要输出对应的长度即可。
- 你算法的时间复杂度应该为 O(n2) 。

进阶: 你能将算法的时间复杂度降低到 O(n log n) 吗?

```go
func lengthOfLIS(nums []int) int {
}
```

## 解题思路

## 题解

```go
func lengthOfLIS(nums []int) int {
    rst := make([]int, len(nums))
    for i := range rst {
        rst[i] = 1
    }

    for i := 1; i < len(nums); i++ {
        for j:=0; j < i; j++ {
            if nums[j] < nums[i] {
                rst[i] = max(rst[i], rst[j] + 1)
            }
        }
    }

    maxV := 0
    for _,v := range rst {
        if v > maxV {
            maxV = v
        }
    }

    return maxV
}

func max(x, y int) int {
    if x > y {
        return x
    }
    return y
}
```
