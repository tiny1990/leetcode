# 78. 子集
给定一组不含重复元素的整数数组 nums，返回该数组所有可能的子集（幂集）。  

说明：解集不能包含重复的子集。  

示例:
```
输入: nums = [1,2,3]
输出:
[
  [3],
  [1],
  [2],
  [1,2,3],
  [1,3],
  [2,3],
  [1,2],
  []
]
```

```go
func subsets(nums []int) [][]int {
}
```

## 解题思路


## 题解

```go
func subsets(nums []int) [][]int {

    rst := make([][]int,0)
    helper(&rst,nums, make([]int,0),0)

    return rst
}

func helper(rst *[][]int,nums []int, line []int, pos int) {

    line_copy := append(line[:0:0], line...)
    *rst = append(*rst, line_copy)

    for i := pos; i < len(nums); i++ {
        line_copy = append(line_copy, nums[i])
        helper(rst, nums, line_copy, i+1)
        line_copy = line_copy[0:len(line_copy)-1]
    }
}

```
