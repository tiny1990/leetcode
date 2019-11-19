# 15. 三数之和
给定一个包含 n 个整数的数组 nums，判断 nums 中是否存在三个元素 a，b，c ，使得 a + b + c = 0 ？找出所有满足条件且不重复的三元组。  

注意：答案中不可以包含重复的三元组。
```
例如, 给定数组 nums = [-1, 0, 1, 2, -1, -4]，

满足要求的三元组集合为：

[
  [-1, 0, 1],
  [-1, -1, 2]
]
```


```go
func threeSum(nums []int) [][]int {
}
```

## 解题思路

## 题解

```go
func threeSum(nums []int) [][]int {

    sort.Ints(nums)
    length := len(nums)

    if length < 3 || nums[0] > 0 || nums[length - 1] < 0 {
        return nil
    }

    var result [][]int
    for i:=0; i< length-2; i++ {

        if i>0 && nums[i] == nums[i-1] {
            continue
        }

        low ,high := i+1, len(nums)-1
        for low < high {
            sum := nums[i] + nums[low] + nums[high]
            if sum == 0 {
                result = append(result,[]int{nums[i], nums[low], nums[high]})
                for low+1 < high && nums[low] == nums[low+1] {
                    low++
                }
                for low < high -1 && nums[high] == nums[high-1] {
                    high--
                }
                low++
                high--
            } else if sum > 0 {
                high--
            } else {
                low++
            }
        }
    }
    return result
}
```