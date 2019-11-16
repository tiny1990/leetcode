# 349. 两个数组的交集
给定两个数组，编写一个函数来计算它们的交集。

示例 1:
```
输入: nums1 = [1,2,2,1], nums2 = [2,2]
输出: [2]
```
示例 2:
```
输入: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
输出: [9,4]
```
说明:  

输出结果中的每个元素一定是唯一的。  
我们可以不考虑输出结果的顺序。  

```go
func intersection(nums1 []int, nums2 []int) []int {
}
```

## 解题思路
num1 放入map  
num2 遍历知否存在即可  
golang中没有set

## 题解

```go
func intersection(nums1 []int, nums2 []int) []int {
    
    map1 := make(map[int]int)
    for i, v := range nums1 {
        map1[v] = i
    }

    map2 := make(map[int]int)
    for _,val := range nums2 {
        if _, ok := map1[val]; ok {
            map2[val] = val
        }
    }

    rtn := make([]int,0)
    for k, _ := range map2 {
        rtn = append(rtn,k)
    }

    return rtn
}

```
