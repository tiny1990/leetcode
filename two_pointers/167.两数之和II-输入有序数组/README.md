# 167. 两数之和 II - 输入有序数组
给定一个已按照升序排列 的有序数组，找到两个数使得它们相加之和等于目标数。  

函数应该返回这两个下标值 index1 和 index2，其中 index1 必须小于 index2。  

说明:

- 返回的下标值（index1 和 index2）不是从零开始的。
- 你可以假设每个输入只对应唯一的答案，而且你不可以重复使用相同的元素。
示例:
```
输入: numbers = [2, 7, 11, 15], target = 9
输出: [1,2]
解释: 2 与 7 之和等于目标数 9 。因此 index1 = 1, index2 = 2 。
```

```go
func twoSum(numbers []int, target int) []int {
}
```

## 解题思路

## 题解

```go
func twoSum(numbers []int, target int) []int {

    i,j := 0, len(numbers)-1

    for i < j {
        s := numbers[i] + numbers[j]
        if s > target {
            j--
        } else if s < target  {
            i++
        } else {
            return []int{i+1,j+1}
        }
    }
    return nil
}

```
-------
```rust
impl Solution {
    pub fn two_sum(numbers: Vec<i32>, target: i32) -> Vec<i32> {
        let mut i: usize = 0;
        let mut j: usize = (numbers.len() - 1) as usize;

        while i < j {
            let sum = numbers[i] + numbers[j];
            if sum > target {
                j = j - 1;
            } else if sum < target {
                i = i + 1;
            } else {
                return vec![(i + 1) as i32, (j + 1) as i32];
            }
        }
        return vec![];
    }
}
```
