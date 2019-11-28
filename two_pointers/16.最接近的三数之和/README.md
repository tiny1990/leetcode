# 16. 最接近的三数之和
给定一个包括 n 个整数的数组 nums 和 一个目标值 target。找出 nums 中的三个整数，使得它们的和与 target 最接近。返回这三个数的和。假定每组输入只存在唯一答案。  

```
例如，给定数组 nums = [-1，2，1，-4], 和 target = 1.

与 target 最接近的三个数的和为 2. (-1 + 2 + 1 = 2).  
```


```go
func threeSumClosest(nums []int, target int) int {
}
```

## 解题思路

## 题解

```go
func threeSumClosest(nums []int, target int) int {
    sort.Ints(nums)

    rtn := nums[0] + nums[1] + nums[2]

    for i:=0; i<len(nums)-2; i++ {
        l,h := i+1, len(nums)-1

        for l < h {
            sum := nums[i] + nums[l] + nums[h]

            if math.Abs(float64(target - sum)) < math.Abs(float64(target - rtn)) {
                rtn = sum
            }
            if sum < target {
                l++
            } else if sum > target {
                h--
            } else {
                return rtn
            }
        }
    }
    return rtn

}    
```
