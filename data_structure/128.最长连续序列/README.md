# 128. 最长连续序列
给定一个未排序的整数数组，找出最长连续序列的长度。  

要求算法的时间复杂度为 O(n)。  

示例:
```
输入: [100, 4, 200, 1, 3, 2]
输出: 4
解释: 最长连续序列是 [1, 2, 3, 4]。它的长度为 4。
```

```go
func longestConsecutive(nums []int) int {
}
```

## 解题思路
很有趣的一个题

## 题解

```go
func longestConsecutive(nums []int) int {
    store := make(map[int]bool)
    for _, v := range nums {
        store[v] = true
    }

    longest := 0

    for _, v := range nums {
        down := v -1
        for store[down] {
            delete(store, down)
            down--
        }
        up := v + 1
        for store[up] {
            delete(store, up)
            up++
        }
        longest = max(longest, up - down -1)
    }
    return longest
}

func max(n1 int , n2 int) int {
    if n1 > n2 {
        return n1
    }
    return n2
}

```
