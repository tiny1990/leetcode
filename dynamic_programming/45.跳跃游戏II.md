# 45. 跳跃游戏 II
给定一个非负整数数组，你最初位于数组的第一个位置。  

数组中的每个元素代表你在该位置可以跳跃的最大长度。  

你的目标是使用最少的跳跃次数到达数组的最后一个位置。  

示例:
```
输入: [2,3,1,1,4]
输出: 2
解释: 跳到最后一个位置的最小跳跃数是 2。
     从下标为 0 跳到下标为 1 的位置，跳 1 步，然后跳 3 步到达数组的最后一个位置。
```

说明:
```
假设你总是可以到达数组的最后一个位置。
```

```go
func jump(nums []int) int {
}
```

## 解题思路
dp解题思路，用数组记录每一步的状态

## 题解

```go
func jump(nums []int) int {

    // init status array
    rst := make([]int, len(nums))
    rst[0] = 0

    for i := 1; i < len(nums); i++ {
        rst[i] = 1 << 31
        for j := 0; j < i; j++  {
            if rst[j] != 1 << 31 && j + nums[j]  >= i {
                rst[i] = rst[j] + 1
                break
            }
        }
    }
    return rst[len(nums)-1]
}
```
