# 674. 最长连续递增序列
给定一个未经排序的整数数组，找到最长且连续的的递增序列。  

示例 1:
```
输入: [1,3,5,4,7]
输出: 3
解释: 最长连续递增序列是 [1,3,5], 长度为3。
尽管 [1,3,5,7] 也是升序的子序列, 但它不是连续的，因为5和7在原数组里被4隔开。 
```
示例 2:
```
输入: [2,2,2,2,2]
输出: 1
解释: 最长连续递增序列是 [2], 长度为1。
```


```go
func findLengthOfLCIS(nums []int) int {
}
```

## 解题思路

## 题解

```go
func findLengthOfLCIS(nums []int) int {
    if len(nums) == 0 {
        return 0 
    }
    rst := make([]int,len(nums))
    max := 1
    rst[0] = 1

    for i:=1; i < len(nums); i++ {
        rst[i] = 1
        if nums[i] >  nums[i-1] {
            rst[i] = rst[i-1] + 1
        }

        if rst[i] > max {
            max = rst[i]
        }
    }
    return max
}
```