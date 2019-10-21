# 47. 全排列 II
给定一个可包含重复数字的序列，返回所有不重复的全排列。  

示例:
```
输入: [1,1,2]
输出:
[
  [1,1,2],
  [1,2,1],
  [2,1,1]
]
```


```go
func permuteUnique(nums []int) [][]int {
}
```

## 解题思路
- dfs 需要set判重
- 使用下标判断是否使用过而不是真是value

## 题解

```go
func permuteUnique(nums []int) [][]int {

    // 排序使得相同的value连续
    sort.Ints(nums)

    rst  := make([][]int, 0)
    list := make([]int, 0)
    set := make(map[int]bool, 0)

    help(&rst, list, set, nums)

    return rst
}

func help(rst *[][]int, list []int, set map[int]bool, nums [][]int) {

    if len(nums) == len(list) {
        *rst = append(*rst, list)
        return 
    }

    list1 := append(list[:0:0], list...)
    set1 := copy_set(set)

    for i := 0; i < len(nums); i++ {
        
        // 判断下标有没有使用过
        if ok, _ := set1[i] {
            continue
        }

        b, _ := set1[i-1]

        // 判断之前的数字使用过 并且 当前和-1的相等跳过
        if i != 0 && b && nums[i] == nums[i-1] {
            continue
        }

        list1 = append(list1, nums[i])
        set1[i] = true
        help(rst, list1, set1, nums)
        list1 = list1[0:len(list1)-1]
        set1[i] = false
    }
}

func copy_set(set map[int]bool) map[int]bool {

    rtn := make(map[int]bool, 0)
    for k,v := range set {
        rtn[k] = v
    }
    return rtn
}
```
