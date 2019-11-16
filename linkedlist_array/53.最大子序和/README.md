# 53. 最大子序和
给定一个整数数组 nums ，找到一个具有最大和的连续子数组（子数组最少包含一个元素），返回其最大和。  

示例:
```
输入: [-2,1,-3,4,-1,2,1,-5,4],
输出: 6
解释: 连续子数组 [4,-1,2,1] 的和最大，为 6。
```


```go
func maxSubArray(nums []int) int {
}
```

## 解题思路

## 题解

```go
func maxSubArray(nums []int) int {
    ans := nums[0]
    sum := 0
    
    for _, v := range nums {
        if sum + v > v {
            sum += v
        } else {
            sum = v
        }
        if ans < sum {
            ans = sum
        }
    }
    
    return ans
}
```
