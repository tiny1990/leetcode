# 42. 接雨水
给定 n 个非负整数表示每个宽度为 1 的柱子的高度图，计算按此排列的柱子，下雨之后能接多少雨水。
![rain-water](./rainwatertrap.png)

示例:
```
输入: [0,1,0,2,1,0,1,3,2,1,2,1]
输出: 6
```

```go
func trap(height []int) int {
}
```

## 解题思路

## 题解

```go
func trap(height []int) int {
    left := 0
    right := len(height) - 1
    
    if right <= 1 {
        return 0
    }

    leftMax := height[left]
    rightMax := height[right]

    ans := 0
    for left < right {
        if leftMax < rightMax {
            left++
            if leftMax > height[left] {
                ans += leftMax - height[left]
            } else {
                leftMax = height[left]
            }
        } else {
            right--
            if rightMax > height[right] {
                ans += rightMax - height[right]
            } else {
                rightMax =  height[right]
            }
        }
    }

    return ans
}
```
