# 39. 组合总和
给定一个无重复元素的数组 candidates 和一个目标数 target ，找出 candidates 中所有可以使数字和为 target 的组合。  

candidates 中的数字可以无限制重复被选取。  

说明：  
- 所有数字（包括 target）都是正整数。
- 解集不能包含重复的组合。 

示例 1:
```
输入: candidates = [2,3,6,7], target = 7,
所求解集为:
[
  [7],
  [2,2,3]
]
```
示例 2:
```
输入: candidates = [2,3,5], target = 8,
所求解集为:
[
  [2,2,2,2],
  [2,3,3],
  [3,5]
]
```


```go
func combinationSum(candidates []int, target int) [][]int {
}
```

## 解题思路

## 题解

```go
func combinationSum(candidates []int, target int) [][]int {

    rst := make([][]int,0)
    line := make([]int,0)
    help(candidates, line, 0, 0, target, &rst)

    return rst

}

func help(candidates []int, line []int,pos int, sum int, target int, rst *[][]int) {

    if sum == target {
        *rst = append(*rst,line)
        return
    }
    if sum > target {
        return
    }

    for i := pos; i < len(candidates); i++ {
        line1 := append(line[:0:0],line...)
        line1 = append(line1,candidates[i])
        tmp := sum + candidates[i]
        help(candidates, line1, i, tmp, target, rst)
    }
}
```
