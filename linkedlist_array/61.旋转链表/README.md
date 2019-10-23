# 61. 旋转链表
给定一个链表，旋转链表，将链表每个节点向右移动 k 个位置，其中 k 是非负数。

示例 1:
```
输入: 1->2->3->4->5->NULL, k = 2
输出: 4->5->1->2->3->NULL
解释:
向右旋转 1 步: 5->1->2->3->4->NULL
向右旋转 2 步: 4->5->1->2->3->NULL
```
示例 2:
```
输入: 0->1->2->NULL, k = 4
输出: 2->0->1->NULL
解释:
向右旋转 1 步: 2->0->1->NULL
向右旋转 2 步: 1->2->0->NULL
向右旋转 3 步: 0->1->2->NULL
向右旋转 4 步: 2->0->1->NULL
```

```go
func rotateRight(head *ListNode, k int) *ListNode {
}
```

## 解题思路
稍后写

## 题解

```go
func rotateRight(head *ListNode, k int) *ListNode {
    if head == nil {
        return nil
    }

    cnt := getLinkedLength(head)
    k = k % cnt

    dummy := &ListNode {
        Next: head,
    }

    head = dummy
    for i:=0; i < k; i++ {
        head = head.Next
    }
    tail := dummy

    for head.Next != nil {
        head = head.Next
        tail = tail.Next
    }

    head.Next = dummy.Next
    dummy.Next = tail.Next
    tail.Next = nil

    return dummy.Next
}

func getLinkedLength(head *ListNode) int {
    cnt := 0
    for head != nil {
        cnt++
        head = head.Next
    }
    return cnt
}
```
