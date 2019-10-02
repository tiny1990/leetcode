# 46. 全排列
给定一个没有重复数字的序列，返回其所有可能的全排列。  

示例:  

输入: ```[1,2,3]```
输出:
```
[
  [1,2,3],
  [1,3,2],
  [2,1,3],
  [2,3,1],
  [3,1,2],
  [3,2,1]
]
```

```go
func permute(nums []int) [][]int {
}
```

## 解题思路
注意点:
- set去重
- golang用map代替
## 题解

```go
func permute(nums []int) [][]int {
    rst := make([][]int, 0)
    line := make([]int, 0)
    set := make(map[int]int, 0)

    help(nums,line,set,&rst)

    return rst
}

func help(nums []int, line []int, set map[int]int ,rst *[][]int) {

    if len(line) == len(nums) {
        *rst = append(*rst,line)
    }

    line1 := append(line[:0:0],line...)
    set1 := copy(set)

    for i:=0; i < len(nums); i++ {
        if _,ok := set1[nums[i]]; ok {
            continue
        }
        line1  = append(line1,nums[i])
        set1[nums[i]] = i
        help(nums,line1,set1,rst)

        // 恢复
        line1 = line1[0:len(line1)-1]
        delete(set1,nums[i])
    }
}

// copy mao
func copy(rst map[int]int) map[int]int {
    rtn := make(map[int]int, 0)
    for k, v := range rst {
        rtn[k] = v
    }
    return rtn
}

```
