# 4. 寻找两个有序数组的中位数
给定两个大小为 m 和 n 的有序数组 nums1 和 nums2。  

请你找出这两个有序数组的中位数，并且要求算法的时间复杂度为 O(log(m + n))。 

你可以假设 nums1 和 nums2 不会同时为空。  

示例 1:
```
nums1 = [1, 3]
nums2 = [2]

则中位数是 2.0
```
示例 2:
```
nums1 = [1, 2]
nums2 = [3, 4]

则中位数是 (2 + 3)/2 = 2.5
```
```go
func findMedianSortedArrays(nums1 []int, nums2 []int) float64 {
}
```

## 解题思路
写一个函数找出第k大的数

## 题解

```go
func findMedianSortedArrays(nums1 []int, nums2 []int) float64 {
    k := len(nums1) + len(nums2)
    if k % 2 == 0 {
       return float64(findkth(nums1,0,nums2,0,k/2) + findkth(nums1,0,nums2,0,k/2+1)) /2.0
    } 
    return float64(findkth(nums1,0,nums2,0,k/2+1)) / 1.0
}

func findkth(nums1 []int, n1start int, nums2 []int, n2start int, k int) int {
    if n1start >= len(nums1) {
        return nums2[n2start + k -1]
    }
    if n2start >= len(nums2) {
        return nums1[n1start + k -1]
    }

    if k == 1 {
        if nums1[n1start] > nums2[n2start] {
           return  nums2[n2start]
        } else {
            return nums1[n1start] 
        }
    }

    key1 := 1<<31
    if n1start + k /2 - 1 < len(nums1) {
        key1 = nums1[n1start + k /2 - 1]
    }

    key2 := 1<<31
    if n2start + k/2 -1 < len(nums2) {
        key2 = nums2[n2start + k/2 -1]
    }
    
    if key1 < key2 {
        return findkth(nums1,n1start + k /2 , nums2,n2start, k - k/2 )
    } else {
        return findkth(nums1,n1start , nums2,n2start + k/2 , k - k/2 )
    }

}
```
