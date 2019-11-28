# 905. 按奇偶排序数组
给定一个非负整数数组 A，返回一个数组，在该数组中， A 的所有偶数元素之后跟着所有奇数元素。  

你可以返回满足此条件的任何数组作为答案。  

示例：
```
输入：[3,1,2,4]
输出：[2,4,3,1]
输出 [4,2,3,1]，[2,4,1,3] 和 [4,2,1,3] 也会被接受。
```

提示：
```
1 <= A.length <= 5000
0 <= A[i] <= 5000
```

```go
func sortArrayByParity(A []int) []int {
}
```

## 解题思路

## 题解

```go
func sortArrayByParity(A []int) []int {
    if A == nil || len(A) == 0 {
        return A
    }
    l, r := 0, len(A) - 1

    for l < r {
        for l <= r && A[l] % 2 ==0 {
            l++
        }
        for l <= r && A[r] % 2 == 1 {
            r--
        }
        if l <= r {
            A[l], A[r] = A[r], A[l]
            // l++
            // r--
            // 注释地方可以较小一次判断
            // 对性能无关紧要
        }
    }
    return A
}
```