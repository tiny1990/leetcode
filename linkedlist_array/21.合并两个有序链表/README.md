# 21. 合并两个有序链表
将两个有序链表合并为一个新的有序链表并返回。新链表是通过拼接给定的两个链表的所有节点组成的。   

示例：
```
输入：1->2->4, 1->3->4
输出：1->1->2->3->4->4
```

```go
func mergeTwoLists(l1 *ListNode, l2 *ListNode) *ListNode {
}
```

## 解题思路

## 题解

```go
func mergeTwoLists(l1 *ListNode, l2 *ListNode) *ListNode {
    if l1 == nil {
        return l2
    } else if l2 == nil {
        return l1
    } else if l1.Val >= l2.Val {
        l2.Next = mergeTwoLists(l1, l2.Next)
        return l2
    } else {
        l1.Next = mergeTwoLists(l1.Next, l2)
        return l1
    }
}
```
