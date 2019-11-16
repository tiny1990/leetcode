# 148. 排序链表
在 O(n log n) 时间复杂度和常数级空间复杂度下，对链表进行排序。  

示例 1:
```
输入: 4->2->1->3
输出: 1->2->3->4
```
示例 2:
```
输入: -1->5->3->4->0
输出: -1->0->3->4->5
```
```go
func sortList(head *ListNode) *ListNode {
}
```

## 解题思路
二分法

## 题解

```go
func sortList(head *ListNode) *ListNode {
    if head == nil || head.Next == nil {
        return head
    }
    mid := findMid(head)
    right := sortList(mid.Next)
    mid.Next = nil

    left := sortList(head)
    
    return  merge(left , right)

}

func merge(list1, list2 *ListNode) *ListNode {

    dummy := &ListNode{}
    tail := dummy

    for list1 != nil && list2 != nil {
        if list1.Val > list2.Val {
            tail.Next = list2
            list2 = list2.Next
        } else {
            tail.Next = list1
            list1 = list1.Next
        }
        tail = tail.Next
    }

    if list1 != nil {
        tail.Next = list1
    }

    if list2 != nil {
        tail.Next = list2
    }

    return dummy.Next

}

func findMid(head *ListNode) *ListNode {
    slow := head
    fast := head.Next

    for fast != nil && fast.Next != nil {
        slow = slow.Next
        fast = fast.Next.Next
    }
    return slow
}

```
